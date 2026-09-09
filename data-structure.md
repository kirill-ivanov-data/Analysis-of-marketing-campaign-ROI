### ad_revenue_raw (Сирі дані про доходи від реклами)

Містить деталізовану інформацію про рекламні покази, доходи з подій, характеристики пристроїв та поведінку користувачів.

| Поле (Column) | Тип даних | Опис |
| :--- | :--- | :--- |
| `firebase_analytic_app_id` | `STRING` | Ідентифікатор застосунку у Firebase |
| `firebase_personal_token` | `STRING` | Персональний токен Firebase |
| `lib_id` | `STRING` | Ідентифікатор бібліотеки |
| `analytics_installation_id` | `STRING` | Унікальний ID встановлення для аналітики |
| `advertising_id` | `STRING` | Рекламний ідентифікатор пристрою (IDFA/GAID) |
| `app_id` | `STRING` | Унікальний ідентифікатор застосунку |
| `media_source` | `STRING` | Джерело трафіку (рекламна мережа) |
| `campaign_id` | `INTEGER` | Ідентифікатор рекламної кампанії |
| `campaign_name` | `STRING` | Назва рекламної кампанії |
| `ad_group_id` | `INTEGER` | Ідентифікатор групи оголошень |
| `ad_group_name` | `STRING` | Назва групи оголошень |
| `creative_id` | `INTEGER` | Ідентифікатор креативу |
| `country` | `STRING` | Країна користувача |
| `install_date` | `TIMESTAMP` | Дата та час встановлення застосунку |
| `ip` | `STRING` | IP-адреса користувача |
| `locale` | `STRING` | Мовні та регіональні налаштування пристрою |
| `device_model` | `STRING` | Модель пристрою |
| `city` | `STRING` | Місто користувача |
| `timestamp` | `TIMESTAMP` | Точний час події |
| `event_revenue_usd` | `FLOAT` | Дохід від події в USD |
| `event_date` | `TIMESTAMP` | Дата події |
| `event_name` | `STRING` | Назва події |
| `ad_format` | `STRING` | Формат показаної реклами (наприклад, banner, interstitial, reward) |
| `app_version` | `STRING` | Версія застосунку |
| `session_number` | `INTEGER` | Порядковий номер сесії користувача |
| `network_subtype` | `STRING` | Підтип рекламної мережі |
| `network_type` | `STRING` | Тип рекламної мережі |
| `device_code` | `STRING` | Код пристрою |
| `ad_unit_test_name` | `STRING` | Тестова назва рекламного блоку |
| `ad_unit_name` | `STRING` | Назва рекламного блоку |
| `placement` | `STRING` | Місце розміщення реклами |
| `network` | `STRING` | Назва рекламної мережі, через яку відбувся показ |
| `waterfall_name` | `STRING` | Назва водоспаду (waterfall) у медіації |
| `platform` | `STRING` | Платформа (iOS / Android) |
| `network_placement` | `STRING` | Розміщення всередині конкретної мережі |
| `ad_unit_id` | `STRING` | Ідентифікатор рекламного блоку |
| `web_customer_id` | `STRING` | Ідентифікатор вебкористувача |
| `aoa_shown_before_paywall` | `INTEGER` | Кількість показів App Open Ads (реклами при відкритті) до появи пейволу |
| `time_to_paywall` | `INTEGER` | Час до показу пейволу |
| `os_version` | `STRING` | Версія операційної системи |
| `connection_type` | `STRING` |  |
| `brand` | `STRING` | Бренд пристрою |
| `click_to_pay_time` | `INTEGER` | Час від кліку до оплати |
| `gdpr_consent_status` | `STRING` | Статус згоди GDPR (на обробку даних) |
| `session_length_first` | `INTEGER` | Тривалість першої сесії |
| `storage_total` | `INTEGER` | Загальний обсяг пам'яті на пристрої |
| `hamon_version` | `STRING` | Версія внутрішнього модуля/бібліотеки (Hamon) |
| `inters_shown_before_paywall` | `INTEGER` | Кількість міжсторінкової реклами (interstitials), показаної до пейволу |
| `paywall_conversion_time` | `INTEGER` | Час, витрачений на конверсію на пейволі |
| `manufacturer` | `STRING` | Виробник пристрою |
| `storage_free` | `INTEGER` | Вільний обсяг пам'яті на пристрої |
| `screen_resolution` | `STRING` | Роздільна здатність екрана |
| `carrier` | `STRING` | Мобільний оператор |
| `ram_total_bytes` | `INTEGER` | Загальний обсяг оперативної пам'яті в байтах |
| `actions_before_paywall` | `INTEGER` | Кількість дій користувача до показу пейволу |
| `taps_count_first_30s` | `INTEGER` | Кількість натискань на екран у перші 30 секунд |
| `appsflyer_id` | `STRING` | Унікальний ідентифікатор пристрою в AppsFlyer |

---
### cost_table (Витрати на рекламу)

Містить дані про щоденні витрати на рекламні кампанії, покази, кліки та бюджети в розрізі джерел трафіку та географії.

| Поле (Column) | Тип даних | Опис |
| :--- | :--- | :--- |
| `date` | `STRING` | Дата витрат на рекламу |
| `app_id` | `STRING` | Унікальний ідентифікатор застосунку |
| `campaign` | `STRING` | Назва рекламної кампанії |
| `campaign_id` | `INTEGER` | Ідентифікатор рекламної кампанії |
| `adset` | `STRING` | Назва групи оголошень (adset) |
| `adset_id` | `INTEGER` | Ідентифікатор групи оголошень |
| `media_source` | `STRING` | Джерело трафіку (рекламна мережа) |
| `country_code` | `STRING` | Код країни |
| `city` | `STRING` | Місто |
| `cost` | `FLOAT` | Сума витрат у локальній валюті |
| `cost_currency` | `STRING` | Валюта витрат (наприклад, EUR, GBP) |
| `cost_usd` | `FLOAT` | Сума витрат, конвертована в USD |
| `impressions` | `INTEGER` | Кількість показів реклами |
| `clicks` | `INTEGER` | Кількість кліків по рекламі |
| `campaign_ad_network_type` | `STRING` | Тип рекламної мережі кампанії |
| `customer_id` | `STRING` | Ідентифікатор клієнта (рекламного акаунта) |
| `most_specific_location` | `STRING` | Найбільш точне місцезнаходження (таргетинг) |
| `budget` | `FLOAT` | Бюджет кампанії у локальній валюті |
| `budget_usd` | `FLOAT` | Бюджет кампанії, конвертований в USD |

---
### in_app_events_report (Події всередині застосунку та покупки)

Містить детальні дані про дії користувачів у застосунку, зокрема інформацію про оформлення підписок, транзакції та конверсії на пейволі.

| Поле (Column) | Тип даних | Опис |
| :--- | :--- | :--- |
| `firebase_analytic_app_id` | `STRING` | Ідентифікатор застосунку у Firebase |
| `firebase_personal_token` | `STRING` | Персональний токен Firebase |
| `lib_id` | `STRING` | Ідентифікатор бібліотеки |
| `analytics_installation_id` | `STRING` | Унікальний ID встановлення для аналітики |
| `advertising_id` | `STRING` | Рекламний ідентифікатор пристрою (IDFA/GAID) |
| `app_id` | `STRING` | Унікальний ідентифікатор застосунку |
| `media_source` | `STRING` | Джерело трафіку (рекламна мережа) |
| `campaign_id` | `INTEGER` | Ідентифікатор рекламної кампанії |
| `campaign_name` | `STRING` | Назва рекламної кампанії |
| `ad_group_id` | `INTEGER` | Ідентифікатор групи оголошень |
| `ad_group_name` | `STRING` | Назва групи оголошень |
| `creative_id` | `INTEGER` | Ідентифікатор креативу |
| `country` | `STRING` | Країна користувача |
| `install_date` | `TIMESTAMP` | Дата та час встановлення застосунку |
| `ip` | `STRING` | IP-адреса користувача |
| `locale` | `STRING` | Мовні та регіональні налаштування пристрою |
| `device_model` | `STRING` | Модель пристрою |
| `city` | `STRING` | Місто користувача |
| `timestamp` | `TIMESTAMP` | Точний час події |
| `event_revenue_usd` | `FLOAT` | Дохід від події в USD (від покупок/підписок) |
| `event_date` | `TIMESTAMP` | Дата події |
| `event_name` | `STRING` | Назва події (наприклад, purchase, trial_started) |
| `order_id` | `STRING` | Унікальний ідентифікатор замовлення/транзакції |
| `product_id` | `STRING` | Ідентифікатор придбаного продукту |
| `subscription_type` | `STRING` | Тип підписки (наприклад, тижнева, річна) |
| `purchase_token` | `STRING` | Токен транзакції для верифікації покупки |
| `app_version` | `STRING` | Версія застосунку |
| `trial_duration` | `INTEGER` | Тривалість безкоштовного пробного періоду (у днях) |
| `session_number` | `INTEGER` | Порядковий номер сесії користувача |
| `voided_source` | `STRING` | Джерело скасування покупки (повернення коштів) |
| `voided_quantity` | `INTEGER` | Кількість скасованих покупок/підписок |
| `voided_reason` | `STRING` | Причина скасування або повернення |
| `network_subtype` | `STRING` | Підтип рекламної мережі |
| `network_type` | `STRING` | Тип рекламної мережі |
| `device_code` | `STRING` | Код пристрою |
| `sub_price` | `FLOAT` | Вартість підписки |
| `email` | `STRING` | Email-адреса користувача (якщо доступна) |
| `web_customer_id` | `STRING` | Ідентифікатор вебкористувача |
| `paywall_conversion_time` | `INTEGER` | Час, витрачений на конверсію на пейволі |
| `aoa_shown_before_paywall` | `INTEGER` | Кількість показів App Open Ads до появи пейволу |
| `time_to_paywall` | `INTEGER` | Час до показу пейволу |
| `hamon_version` | `STRING` | Версія внутрішнього модуля/бібліотеки (Hamon) |
| `connection_type` | `STRING` | Тип інтернет-з'єднання (Wi-Fi, 4G, 5G) |
| `inters_shown_before_paywall` | `INTEGER` | Кількість міжсторінкової реклами (interstitials) до пейволу |
| `gdpr_consent_status` | `STRING` | Статус згоди GDPR (на обробку даних) |
| `os_version` | `STRING` | Версія операційної системи |
| `session_length_first` | `INTEGER` | Тривалість першої сесії |
| `click_to_pay_time` | `INTEGER` | Час від кліку до оплати |
| `brand` | `STRING` | Бренд пристрою |
| `storage_free` | `INTEGER` | Вільний обсяг пам'яті на пристрої |
| `storage_total` | `INTEGER` | Загальний обсяг пам'яті на пристрої |
| `manufacturer` | `STRING` | Виробник пристрою |
| `screen_resolution` | `STRING` | Роздільна здатність екрана |
| `carrier` | `STRING` | Мобільний оператор |
| `ram_total_bytes` | `INTEGER` | Загальний обсяг оперативної пам'яті в байтах |
| `actions_before_paywall` | `INTEGER` | Кількість дій користувача до показу пейволу |
| `taps_count_first_30s` | `INTEGER` | Кількість натискань на екран у перші 30 секунд |
| `appsflyer_id` | `STRING` | Унікальний ідентифікатор пристрою в AppsFlyer |

---
### non_org_installs_report (Звіт про неорганічні встановлення)

Містить дані про встановлення застосунку, залучені через платні джерела трафіку (неорганічні), деталі атрибуції рекламних кампаній та технічні характеристики пристроїв.

| Поле (Column) | Тип даних | Опис |
| :--- | :--- | :--- |
| `analytics_installation_id` | `STRING` | Унікальний ID встановлення для аналітики |
| `advertising_id` | `STRING` | Рекламний ідентифікатор пристрою (IDFA/GAID) |
| `firebase_analytic_app_id` | `STRING` | Ідентифікатор застосунку у Firebase |
| `firebase_personal_token` | `STRING` | Персональний токен Firebase |
| `lib_id` | `STRING` | Ідентифікатор бібліотеки |
| `media_source` | `STRING` | Джерело трафіку (рекламна мережа) |
| `app_id` | `STRING` | Унікальний ідентифікатор застосунку |
| `ad_event_id` | `STRING` | Ідентифікатор рекламної події |
| `conversion_metric` | `STRING` | Метрика конверсії |
| `timestamp` | `TIMESTAMP` | Точний час події |
| `campaign_type` | `STRING` | Тип рекламної кампанії |
| `campaign_id` | `INTEGER` | Ідентифікатор рекламної кампанії |
| `campaign_name` | `STRING` | Назва рекламної кампанії |
| `ad_type` | `STRING` | Тип реклами |
| `external_customer_id` | `INTEGER` | Зовнішній ідентифікатор клієнта |
| `location` | `INTEGER` | Ідентифікатор локації/географії |
| `network_type` | `STRING` | Тип рекламної мережі |
| `network_subtype` | `STRING` | Підтип рекламної мережі |
| `video_id` | `STRING` | Ідентифікатор відеокреативу |
| `keyword` | `STRING` | Ключове слово, за яким відбувся показ/клік |
| `match_type` | `STRING` | Тип відповідності ключового слова |
| `placement` | `STRING` | Місце розміщення реклами |
| `ad_group_id` | `INTEGER` | Ідентифікатор групи оголошень |
| `ad_group_name` | `STRING` | Назва групи оголошень |
| `creative_id` | `INTEGER` | Ідентифікатор креативу |
| `interaction_type` | `STRING` | Тип взаємодії з рекламою (клік, перегляд) |
| `country` | `STRING` | Країна користувача |
| `city` | `STRING` | Місто користувача |
| `install_date` | `TIMESTAMP` | Дата та час встановлення застосунку |
| `app_version` | `STRING` | Версія застосунку |
| `ip` | `STRING` | IP-адреса користувача |
| `locale` | `STRING` | Мовні та регіональні налаштування пристрою |
| `device_model` | `STRING` | Модель пристрою |
| `device_code` | `STRING` | Код пристрою |
| `web_customer_id` | `STRING` | Ідентифікатор вебкористувача |
| `aoa_shown_before_paywall` | `INTEGER` | Кількість показів App Open Ads до появи пейволу |
| `time_to_paywall` | `INTEGER` | Час до показу пейволу |
| `os_version` | `STRING` | Версія операційної системи |
| `connection_type` | `STRING` | Тип інтернет-з'єднання (Wi-Fi, 4G, 5G) |
| `brand` | `STRING` | Бренд пристрою |
| `click_to_pay_time` | `INTEGER` | Час від кліку до оплати |
| `gdpr_consent_status` | `STRING` | Статус згоди GDPR (на обробку даних) |
| `session_length_first` | `INTEGER` | Тривалість першої сесії |
| `storage_total` | `INTEGER` | Загальний обсяг пам'яті на пристрої |
| `hamon_version` | `STRING` | Версія внутрішнього модуля/бібліотеки (Hamon) |
| `inters_shown_before_paywall` | `INTEGER` | Кількість міжсторінкової реклами (interstitials) до пейволу |
| `paywall_conversion_time` | `INTEGER` | Час, витрачений на конверсію на пейволі |
| `manufacturer` | `STRING` | Виробник пристрою |
| `storage_free` | `INTEGER` | Вільний обсяг пам'яті на пристрої |
| `screen_resolution` | `STRING` | Роздільна здатність екрана |
| `carrier` | `STRING` | Мобільний оператор |
| `ram_total_bytes` | `INTEGER` | Загальний обсяг оперативної пам'яті в байтах |
| `actions_before_paywall` | `INTEGER` | Кількість дій користувача до показу пейволу |
| `taps_count_first_30s` | `INTEGER` | Кількість натискань на екран у перші 30 секунд |
| `appsflyer_id` | `STRING` | Унікальний ідентифікатор пристрою в AppsFlyer |
