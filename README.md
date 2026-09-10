# Analysis-of-marketing-campaign-ROI
### Мета та завдання
Для просування мобільних застосунків бізнес закуповує трафік, сплачуючи рекламним мережам за кожне встановлення. Щоб розуміти, які кампанії окупаються, а які зливають бюджет, потрібна маркетингова вітрина: одна таблиця, у якій зведено разом витрати на рекламу й гроші, що ці кампанії принесли.
Зараз ці дані лежать у чотирьох окремих таблицях у Google BigQuery (обсяг даних: 12+ млн рядків) і ніяк не пов'язані між собою. Завдання полягає в тому, щоб зв'язати їх.


### Логіка по якій міркував
Для оцінки окупності треба від доходів відняти витрати. Зі структури датасета стає зрозуміло, що ми маємо доходи від продажу продукту і від показів реклами всередині нього, а також є таблиця з id користувачів, які прийшли з різних маркетингових кампаній.

Отже, спочатку нам треба окремо зробити джоїн таблиць доходів з таблицею завантажень через рекламу, тим самим зрозумівши, які саме користувачі були отримані не органічно. А потім — згрупувати кампанії і знайти суму доходів для кожної. Також треба зробити групування для таблиці витрат. Наприкінці об'єднати всі три таблиці та зробити фінальні розрахунки. Важливо: на кожному з етапів не слід забувати про наявність пропущених значень (NULL).

**Структура даних:** [data-structure.md](data-structure.md)

**Посилання на дашборд:** https://public.tableau.com/views/test_dashboard_17877627331770/sheet3?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link

**Готова таблиця:** [marketing-campaign-ROI_csv](test_task_csv.csv)

### План роботи:
Створити 4 таблиці, а потім зв'язати їх.
1. cost_mark_capm (Витрати): Знаходимо загальні витрати на кожну рекламну кампанію з урахуванням дати та медіа ресурсу.
2. rev_ad (Доходи з реклами): Отримуємо доходи від показів реклами користувачам, які були залучені не органічно (через LEFT JOIN з таблицею інсталів).
3. rev_in_app (Доходи від продажів): Доходи від продажу всередині продукту (де дохід > 0), отримані від залучених користувачів.
4. Фінальна збірка. Наприкінці ми збираємо всі створені таблиці через FULL OUTER JOIN з використанням USING, щоб отримати усі дні, кампанії та медіа ресурси незалежно від наявності чи відсутності доходу.

### SQL запит

```sql
WITH cost_mark_capm AS ( -- витрати на кожну рекламную компанію
  SELECT
    CAST(date AS DATE) as date
    , campaign_id
    , campaign AS campaign_name
    , media_source
    , SUM(cost_usd) AS sum_cost_usd -- загальні витрати на кожну компанію з урахуванням дати та медіа ресурсу
  FROM `mornhouse-test-environment.test_app_dataset.cost_table`
  GROUP BY 1, 2, 3, 4 -- группуємо за датою, компанією (id та назва) та медіа ресурсом

), rev_ad AS (

  SELECT
    CAST(event_date AS DATE) date -- переводиму у коректний тип даних

    -- така форма з "COALESCE" більш беспечна, тому що:
    --   1. вона захищає від випадків, коли частина даних пропущена в одному стовпці, але є в іншій таблиці.
    --   2. після реєстрації користувач може зробити декілька переглядів реклами, але у таблиці доходів не обов'язково буде вказано, з якої кампанії він прийшов. Проте ця прив'язка завжди є через analytics_installation_id. Тому COALESCE у будь-якому випадку поверне назву кампанії, якщо вона є в базі.

    , COALESCE(ad_rev.campaign_name, org_ins.campaign_name) AS campaign_name
    , COALESCE(ad_rev.campaign_id, org_ins.campaign_id) AS campaign_id
    , COALESCE(ad_rev.media_source, org_ins.media_source) AS media_source
    , SUM(event_revenue_usd) AS revenue_from_advertising_impressions
  FROM `mornhouse-test-environment.test_app_dataset.ad_revenue_raw` AS ad_rev
  -- робимо LEFT JOIN щоб отримати всіх користувачів, яки прибули не органічно, тому що для органічних замість компаній буде null
    LEFT JOIN `mornhouse-test-environment.test_app_dataset.non_org_installs_report` AS org_ins
      ON ad_rev.analytics_installation_id = org_ins.analytics_installation_id -- analytics_installation_id це унікальниї id для кожного користувача та
  GROUP BY 1, 2, 3, 4 -- группуємо за датою, компанією та медіа ресурсом

), rev_in_app AS (

  SELECT
    CAST(event_date AS DATE) date
    , COALESCE(rev_in.campaign_name, org_ins.campaign_name) AS campaign_name
    , COALESCE(rev_in.campaign_id, org_ins.campaign_id) AS campaign_id
    , COALESCE(rev_in.media_source, org_ins.media_source) AS media_source
    , SUM(event_revenue_usd) AS revenue_in_app_event
  FROM `mornhouse-test-environment.test_app_dataset.in_app_events_report` AS rev_in
    LEFT JOIN `mornhouse-test-environment.test_app_dataset.non_org_installs_report` AS org_ins
      ON rev_in.analytics_installation_id = org_ins.analytics_installation_id
  WHERE event_revenue_usd > 0
  GROUP BY 1, 2, 3, 4 -- группуємо за датою, компанією та медіа ресурсом
)


-- Тепер робимо останню таблицю, в якій ми збираємо всі зроблені раніше

SELECT
  cmc.campaign_id
  , campaign_name
  , cmc.media_source
  , cmc.date
  -- надалі ми розраховуємо прибуток шляхом віднімання, тому нам треба позбутися NULL значень, замінивши їх на нулі за допомогою COALESCE (бо математичні операції з NULL дають NULL)
  , COALESCE(sum_cost_usd, 0)
  , COALESCE(revenue_from_advertising_impressions, 0) AS revenue_from_advertising_impressions
  , COALESCE(revenue_in_app_event, 0) AS revenue_in_app_event -- для тих випадків коли немає значень
  , (COALESCE(revenue_from_advertising_impressions, 0) + COALESCE(revenue_in_app_event, 0)) AS total_revenue
  , (COALESCE(revenue_from_advertising_impressions, 0) + COALESCE(revenue_in_app_event, 0)) - COALESCE(sum_cost_usd, 0) AS absolute_payback -- окупність у абсолютних значеннях
  , SAFE_DIVIDE((COALESCE(revenue_from_advertising_impressions, 0) + COALESCE(revenue_in_app_event, 0)), COALESCE(sum_cost_usd, 0)) AS relative_payback -- відносна окупність (використовуємо "SAFE_DIVIDE" для запобігання помилок при діленні на нуль)
FROM cost_mark_capm AS cmc
  FULL OUTER JOIN rev_ad AS ra
    USING (date, campaign_id, campaign_name, media_source)
  FULL OUTER JOIN rev_in_app AS ria
  USING (date, campaign_id, campaign_name, media_source)
```
