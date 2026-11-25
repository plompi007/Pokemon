# Israeli government open vehicle data (data.gov.il / משרד התחבורה) for a "car report by plate" site

Date checked for everything below: **2026-11-25**.

**How this was researched, and the limits.** This session's network blocked data.gov.il, www.data.gov.il, www.gov.il, odata.org.il and over.org.il: curl got proxy 403 and WebFetch got ENOTFOUND. So **no claim below was read live from data.gov.il or gov.il today**. The main evidence is:
- (a) **A raw dump of the data.gov.il CKAN `package_search` API**, snapshot dated 2026-05-06, committed to GitHub at `danielrosehill/Israel-Open-Data-Resources/060526/datasets-raw.json`. It holds 1,194 packages with full CKAN metadata: license_id/title, Frequency, metadata_modified, resource IDs, sizes and datastore_active. It is a machine copy of the primary API, so it is near-primary. It is labelled **"secondary (raw CKAN dump, 2026-05-06)"** below.
- (b) **Automated CKAN ingestion reports**, read from the live API on 2026-10-09, in GitHub repo `giladscore494/tripy` (`data/gov/report.md`, `manifest.json`, `build_status.json`). These give row counts, licence strings, schemas and failures. Labelled **"secondary (tripy CKAN build, 2026-10-09)"**.
- (c) **Field names taken from open-source apps that query the API**: MyCarPortal, info4Car_bot and israel_cars.
- (d) **WebSearch summaries.** These are the weakest evidence.

To upgrade any of this to "verified in primary source", re-run `package_show` / `datastore_search?limit=0` from a network that allows data.gov.il.

---

## 1. Which vehicle datasets exist: IDs, contents, frequency, last update, size

### Takeaway
The Ministry of Transport (משרד התחבורה והבטיחות בדרכים, publishing mailbox `bidata@mot.gov.il`) publishes about 25 vehicle-related datasets on data.gov.il. All are CSV with the CKAN DataStore active, and all are flagged `Frequency: Day, Update: Automat`, refreshed nightly around 02:25–02:36. Together they cover almost everything Carzone-style reports show:
- the active registry, split across two resources
- inactive and scrapped vehicles
- motorcycles, heavy vehicles and public vehicles
- personal import
- ownership history (dates and ownership type only)
- odometer at last test, plus structural, colour, tyre and LPG change flags
- recall notices, plus a per-plate list of vehicles with an open recall
- disability tags
- model specs with WLTP, safety equipment, pollution group and safety rating
- the official new-car **importer price list** (מחירון)

### Cited Findings

**Organisation.** The Ministry of Transport org on data.gov.il held 180 datasets as of 2026-05-06. Its slug is `ministry_of_transport`, and the list API is `package_search?fq=organization:ministry_of_transport&rows=1000`. [danielrosehill README 060526](https://github.com/danielrosehill/Israel-Open-Data-Resources/blob/main/060526/README.md). Confidence: secondary (generated from CKAN API).

**Per-dataset inventory.** Every row below comes from the raw CKAN dump [datasets-raw.json](https://github.com/danielrosehill/Israel-Open-Data-Resources/blob/main/060526/datasets-raw.json) and its index [README](https://github.com/danielrosehill/Israel-Open-Data-Resources/blob/main/060526/README.md). Confidence: secondary (raw CKAN dump, 2026-05-06). License, update frequency and last-modified date sit in the inventory columns. "Size" is the CSV file size; "rows" is the datastore row count from tripy (2026-10-09) where available.

| Dataset (slug) and Hebrew title | Resource ID(s) | What it contains (CKAN `notes`) | License (as shown) | Freq / last modified seen | Size / rows |
|---|---|---|---|---|---|
| `private-and-commercial-vehicles`: **מספרי רישוי של כלי רכב פרטיים ומסחריים** | `053cea08-09bc-40ec-8f7a-156f0677aff3` (main, "מאגר מספרי רישוי של כלי רכב"); `0866573c-40cd-4ca8-91d2-9dd2d7a492e5` ("…- המשך", continuation) | Active private vehicles from model year 1996+ and active commercial vehicles up to 3,500 kg from model year 1998+. Remark: "הנתונים במאגר מתעדכנים ברמה יומית עד השעה 09:00 בבוקר. אין להתייחס בשלב זה לתאריך העדכון של הקובץ." | `other-open`, "אחר (פתוח)" | Day / 2026-05-06 | 867 MB + 308 MB; **4,187,011 rows** in 053cea08 per [tripy report](https://github.com/giladscore494/tripy/blob/main/data/gov/report.md) (estimated total, within 2%) |
| `reshev_bitul_sofi`: **כלי רכב שירדו מהכביש ובסטטוס ביטול סופי** | `851ecab1-0622-4dbe-a6c7-f950cf82abf9` (current); `4e6b9724-4c1e-43f0-909a-154d4cc4e046` (2010–2016, lm 2021-11-01); `ec8cbc34-72e1-4b69-9c48-22821ba0bd6c` (2000–2009, lm 2023-05-02) | Vehicles off the road since 2010 in final-cancellation status. Fields listed in notes: מספר רכב, קוד/שם תוצר, קוד/שם דגם, סוג רכב, מועד עליה לכביש, תאריך ביטול, מספר שילדה, תוצר/דגם/מספר מנוע, משקל כולל | other-open | Day / 2026-05-06 | 1,218,960 / 670,293 / 499,791 rows ([tripy](https://github.com/giladscore494/tripy/blob/main/data/gov/report.md)) |
| `rechev_le_pail_with_degem`: **מספרי רישוי של כלי רכב לא פעילים עם קוד דגם** | `f6efe89a-fb3d-43a4-bb61-9bf12a9b9099` | Vehicles with a model code whose licence expired more than 13 months ago, not stolen and not finally cancelled | other-open | Day / 2026-05-06 | 128 MB |
| `rechev_le_pail_without-degem`: **מספרי רישוי של כלי רכב לא פעילים וחסרי קוד דגם** | `6f6acd03-f351-4a8f-8ecf-df792f4f573a` | Same as above, for vehicles without a model code | other-open (per README index) | Day | not read |
| `shinui_mivne`: **היסטוריית כלי רכב פרטיים** | `56063a99-8a3e-4ff4-912e-5966c0279bad` ("(1)"); `bb2355dc-9ec7-4f06-9c3f-3344672171da` ("(2)") | "המאגרים מציגים נתונים אודות כלי רכב פרטיים פעילים החל משנת 2017" | `other-open`, "Other (Open)" | Day / 2026-05-06 | 158 MB + 163 MB |
| `motorcycle`: **מספרי רישוי של כלי רכב דו גלגליים** | `bf9df4e2-d90d-4c0a-a400-19e15af8e95f` | Technical details of active two-wheelers | other-open | Day / 2026-05-06 | 41 MB |
| `heavy-truck`: **כלי רכב מעל 3 וחצי טון וכלי רכב חסרי קוד דגם** | `cd3acc5c-03c3-4c89-9c54-d40f93c0d790` | Semi-trailers, tractors, work vehicles, trucks and buses. Fields: מספר רישוי, מספר שילדה, תקינה אירופאית, שנת ייצור, קוד/שם תוצר, ארץ ייצור, סוג דלק, משקל כולל, שם דגם | other-open | Day / 2026-05-06 | 89 MB |
| `kli_rechev_ciburiim`: **מספרי רישוי של כלי הרכב הציבוריים הפעילים** | `cf29862d-ca25-4691-84f6-1be60dcb4a1e` | Taxis, service taxis (זוטובוסים / מוניות שירות) and paid shuttle buses | other-open | Day / 2026-05-06 | 12.5 MB |
| `bus_fleet`: **ציי רכב אוטובוסים** | `91d298ed-a260-4f93-9d50-d5e3c5b82ce1` | Operator, bus number, stone/bullet-proofing, year, country, **mileage** | other-open | Day / 2026-05-06 | 3 MB |
| `personal_import_vehicles`: **כלי רכב ביבוא אישי** | `03adc637-b6fe-402b-9937-7c3d3afc9140` | Active personal-import vehicles. Fields: מספר רכב, שילדה, תוצר, סוג רכב, דגם, משקל, שנת ייצור, נפח מנוע, ארץ תוצר, דגם מנוע, תאריך טסט אחרון, תוקף רישוי, **סוג יבוא (משומש/חדש)**, מועד עליה לכביש | other-open | Day / 2026-05-06 | 5 MB |
| `degem-rechev-wltp`: **תוצרים ודגמים של כלי רכב פרטי ומסחרי** | `142afde2-6228-49f9-8a29-9b6c3a0cbe40` (WLTP models); `5e87a7a1-2f6f-41c1-8aec-7216d52a6cf6` ("מאגר כמויות כלי רכב לפי תוצר, דגם ושנת יצור") | Private models from 1996+ and commercial models from 1998+, "כולל נתוני WLTP" | other-open | Day / 2026-05-06 | 52 MB + 8.6 MB |
| `tozeret`: **תוצרים של כלי הרכב הפעילים** | `d00812f4-58c5-4ce8-b16c-ac13ae52f9d8` | Manufacturer code and name, with and without country, plus country | other-open | Day | 78 KB |
| `recall`: **הודעות יצרני הרכב RECALL** | `2c33523f-87aa-44ec-a736-edbb0a82975e` | "קריאה חוזרת בטיחותית RECALL", at model level | **`cc-by`, Creative Commons Attribution** (license_url opendefinition cc-by) | Day / 2026-05-06; datastore lm 2026-10-09 | **3,628 rows (exact)** ([tripy](https://github.com/giladscore494/tripy/blob/main/data/gov/report.md)) |
| `hagbalat_recall`: **כלי רכב שלא ביצעו ריקול (קריאת שירות)** | `36bf1404-0be4-49d2-82dc-2f1ead4a8b93` | Per plate: vehicles that received an importer recall letter more than six months ago and have not done the fix. Remark: "לרכבים אלה לא ניתן לחדש את רישיון הרכב ולא ניתן לבצע העברת בעלות." | other-open | Day / 2026-05-06 | 31 MB |
| `rechev-tag-nachim`: **כלי רכב עם תג חניה לנכה** | `c8b9f9c8-4612-4068-934f-d4acd2e3c06e` | Plates holding a disabled-parking tag | other-open (per index) | Day | not read |
| `zakaut-hatkana`: **מערכת בטיחות ברכב** | `83bfb278-7be1-4dab-ae2d-40125a923da1` | Plates eligible for a licence-fee discount for having a safety system installed | **cc-by** | Day / 2026-05-06 | 49 MB |
| `mehir_yevuan`: **יבואנים ומחירוני רכב חדש** | `39f455bf-6db0-4926-859d-017f34eacbcb` | "מחירי דגמי כלי רכב חדשים לפי יבואן כפי שנמסר ע"י היבואן… מחירי כלי הרכב של דגמים ממשיכים מתעדכנים פעם בשנה" | other-open (tripy saw "Other (Open)") | Day / 2026-05-06; datastore lm 2026-10-09 | 11.8 MB; **101,824 rows** |
| `vehicles_filters_reduce_emissions`: **כלי רכב שמותקנים בהם מסננים לצמצום פליטת מזהמים** | `7cb2bd95-bf2e-49b6-aea1-fcb5ff6f0473` | Plate, EU standard, year, registration date, filter-install date | other-open | Day | 0.3 MB |
| `hatkana_nekudat_igun`: **כלי רכב המחויבים בהתקנת נקודות עיגון** | `786b33b5-75c4-42a3-a241-b1af3c9ca487` | Plates of vehicles over 3.5 t that must install cargo anchor points | other-open | Day | 3 MB |
| `rechavim_hashmalim`: כמות כלי רכב חשמליים לפי נפה | `07421a4e-5b12-4444-9173-5ca297b31f79` | Aggregate counts | other-open | Day | 4 KB |
| `amount_monthly_closures_vehicles` / `kamut_sgirot_hodshi_rechev_blikoddegem`: monthly new vehicles on the road (with and without model code) | `602ac32d-19c0-4b41-88e0-e3ce8a7e80b7` / `c967097c-3c74-4adf-a732-0fdd2fda56d9` | Aggregate counts | not read | not read | not read |
| Business directories: `musachim` (מוסכים ומכוני רישוי), `socharim` (סוחרי רכב), `shamaim_rechev` (שמאי רכב), `batei-esek` (סחר, יבוא וייצור מוצרי תעבורה) | `bb68386a-a331-4bbc-b668-bba2766d517d`, `eb74ad8c-ffcd-43bb-949c-2244fc8a8651`, `4a434d65-3ca2-45e5-8026-5d9819c3f95c`, `42e73a60-7acc-4c5d-b4ec-b0e468a73c51` | Garages and test stations, licensed dealers, assessors, parts businesses | **cc-by** (all four) | Day / 2026-05-06 | not read |
| `construction_equipment`: כלי צמ"ה | `58dc4654-16b1-42ed-8170-98fadec153ea` | Engineering equipment | not read | not read | not read |

**Field names**, mostly from code that queries the API. Confidence: secondary, from consumer code, not the datastore `fields` array.
- **053cea08, active registry.** Fields: `mispar_rechev, tozeret_cd, sug_degem, tozeret_nm, degem_cd, degem_nm, ramat_gimur, ramat_eivzur_betihuty, kvutzat_zihum, shnat_yitzur, degem_manoa, mivchan_acharon_dt` (last test), `tokef_dt` (licence validity), `baalut` (current ownership type), `misgeret` (VIN/chassis), `tzeva_cd, tzeva_rechev, zmig_kidmi, zmig_ahori, sug_delek_nm, horaat_rishum, moed_aliya_lakvish, kinuy_mishari, rank`. Sources: [israel_cars main.py / tests](https://github.com/digitaloracle/israel_cars), [MyCarPortal data-gov.ts](https://github.com/DaelShloush/MyCarPortal/blob/main/frontend/lib/api/data-gov.ts).
- **0866573c, "המשך".** MyCarPortal reads tyre load and speed codes (`kod_omes_tzmig_kidmi/ahori, kod_mehirut_tzmig_kidmi/ahori`) and `grira_nm` (tow hitch) from it. [MyCarPortal API-REFERENCE.md](https://github.com/DaelShloush/MyCarPortal/blob/main/docs/API-REFERENCE.md) lists `merkav, mishkal_kolel, gorrar`. **Contradiction.** CKAN titles 0866573c as the *continuation* of the plate registry, but apps treat it as an "extended info" table keyed by plate. The exact schema is unverified.
- **56063a99, history (1).** Fields: `mispar_rechev, kilometer_test_aharon` (**odometer at last annual test**), `shinui_mivne_ind, shnui_zeva_ind, shinui_zmig_ind, gapam_ind` (structural change, colour change, tyre change, LPG, all Y/N), `rishum_rishon_dt` (first registration), `mkoriut_nm` (origin, i.e. import-channel type), `mispar_manoa`. Sources: [info4Car_bot enriched_info_formatter.py](https://github.com/YoelTavger/info4Car_bot/blob/main/display/formatters/enriched_info_formatter.py), [MyCarPortal data-gov.ts](https://github.com/DaelShloush/MyCarPortal/blob/main/frontend/lib/api/data-gov.ts).
- **bb2355dc, history (2).** Ownership history, one row per ownership period: `mispar_rechev, baalut_dt` (YYYYMM), `baalut` (type: פרטי / ליסינג / השכרה / חברה / סוחר …). Sources: [israel_cars README](https://github.com/digitaloracle/israel_cars/blob/master/README.md), [info4Car_bot ownership_history_formatter / vehicle_service.py](https://github.com/YoelTavger/info4Car_bot). info4Car_bot filters out `baalut == 'סוחר'` when it counts "יד".
- **142afde2, WLTP model specs, about 90 fields.** Includes `nefah_manoa, koah_sus, mispar_dlatot, mispar_moshavim, mishkal_kolel, automatic_ind, merkav, ramat_gimur, technologiat_hanaa_nm, kosher_grira_*, kvuzat_agra_cd, CO2_WLTP, abs_ind, bakarat_yatzivut_ind, ramat_eivzur_betihuty`, plus about 19 ADAS `_ind` flags (e.g. `bakarat_shyut_adaptivit_ind, zihuy_holchey_regel_ind, nitur_merhak_milfanim_ind, matzlemat_reverse_ind`). Source: [MyCarPortal data-gov.ts and API-REFERENCE.md](https://github.com/DaelShloush/MyCarPortal/blob/main/docs/API-REFERENCE.md). The safety rating (ramat eivzur betihuty), pollution group (kvutzat zihum 1–15) and safety level are also shown by [israel_cars](https://github.com/digitaloracle/israel_cars/blob/master/README.md).
- **36bf1404, open recalls per plate.** `MISPAR_RECHEV, RECALL_ID, SUG_RECALL, TEUR_TAKALA, SUG_TAKALA, TAARICH_PTICHA`. These join to 2c33523f by `RECALL_ID`. [MyCarPortal data-gov.ts](https://github.com/DaelShloush/MyCarPortal/blob/main/frontend/lib/api/data-gov.ts)
- **2c33523f, recall notices.** `RECALL_ID, TOZAR_CD, TOZAR_TEUR, DEGEM, SHNAT_RECALL, BUILD_BEGIN_A, BUILD_END_A, SUG_RECALL, SUG_TAKALA, TEUR_TAKALA, OFEN_TIKUN, TKINA_EU, YEVUAN_TEUR, TELEPHONE, WEBSITE`. [tripy report](https://github.com/giladscore494/tripy/blob/main/data/gov/report.md). Confidence: secondary (read from the datastore on 2026-10-09).
- **39f455bf, price list.** `semel_yevuan, shem_yevuan, sug_degem, tozeret_cd, tozeret_nm, degem_cd, degem_nm, shnat_yitzur, mehir, kinuy_mishari`. Sample row: Renault "טווינגו", 1996, `mehir` 54,950, importer קרסו מוטורס. [tripy report](https://github.com/giladscore494/tripy/blob/main/data/gov/report.md)
- **c8b9f9c8, disability tag.** Field names **contain spaces**: `"MISPAR RECHEV"`, `"TAARICH HAFAKAT TAG"` (YYYYMMDD), `"SUG TAV"`. [MyCarPortal data-gov.ts comment](https://github.com/DaelShloush/MyCarPortal/blob/main/frontend/lib/api/data-gov.ts)
- **cf29862d, public vehicles.** `mispar_rechev, sug_rechev_nm, mispar_mekomot, bitul_nm, tokef_dt`. [MyCarPortal](https://github.com/DaelShloush/MyCarPortal/blob/main/frontend/lib/api/data-gov.ts)

### Inferences
- For one consumer report, a site needs to join by `mispar_rechev` across 053cea08 (or 0866573c), 56063a99, bb2355dc, 36bf1404 and c8b9f9c8, with fallbacks to f6efe89a, 6f6acd03, 851ecab1, bf9df4e2, cd3acc5c, cf29862d and 03adc637. It then joins by `tozeret_cd + degem_cd + shnat_yitzur` to 142afde2 (specs) and 39f455bf (original price). Recall notices (2c33523f) join by `RECALL_ID` from 36bf1404. MyCarPortal does exactly this: 7 parallel calls plus 2 dependent ones. [MyCarPortal API-REFERENCE.md](https://github.com/DaelShloush/MyCarPortal/blob/main/docs/API-REFERENCE.md)
- The "history" and "ownership" data covers only **private** vehicles **active since 2017** (CKAN notes). Commercial vehicles, motorcycles and older or scrapped cars have no ownership or odometer history in open data. (My estimate, based on the dataset description.)
- **Price list (מחירון).** The only official government price data is the **importer-reported original list price for new cars** (39f455bf). There is **no official government used-car valuation price list**; Levi Yitzhak and similar lists are commercial. The absence was not confirmed by a search. (My estimate.)

### Gaps
- Exact live record counts were not read today for 0866573c, 56063a99, bb2355dc, 36bf1404, c8b9f9c8, bf9df4e2, cd3acc5c, 142afde2 or 03adc637. Read them with `datastore_search?limit=0`.
- **Vehicle import / customs data** (רשות המסים, משרד הכלכלה personal-import portal) as an open dataset: **not found**. A Ministry of Economy personal-import app exists at [apps.economy.gov.il PersonalImport](https://apps.economy.gov.il/Apps/PersonalImport/Home/Terms_and_conditions/) but was not examined.
- "Green index" (מדד ירוק): beyond `kvutzat_zihum` and `CO2_WLTP`, **not found** as a separate open dataset.
- Accident history, liens (שעבודים), seizures (עיקולים) and stolen status are **not in any open dataset found**. Third-party sites note the lookups do not show liens or seizures ([search summary](https://esekshave.org.il/vehicle-check-by-plate/)). Confidence: secondary.

---

## 2. Access method, API features, rate limits, stability

### Takeaway
All the vehicle resources have `datastore_active: true` and can be queried with CKAN `datastore_search` (filters, q, fields, sort, limit, offset) without any API key. Bulk CSV files exist, but in October 2026 a scripted client found the file download URLs redirecting to accounts.google.com, so in practice bulk reads have to page through the datastore. No official rate limit is documented. Third parties report undocumented throttling and say `datastore_search_sql` is disabled or unreliable.

### Cited Findings
- **Endpoints.** `https://data.gov.il/api/3/action/datastore_search?resource_id=…&filters={"mispar_rechev":…}` works with no auth. CKAN `filters` accepts an array of values. `limit=0` returns only `total`, which can be used for counts. [MyCarPortal data-gov.ts](https://github.com/DaelShloush/MyCarPortal/blob/main/frontend/lib/api/data-gov.ts). Confidence: secondary.
- **What the API dump shows (2026-05-06).** "`status_show` returns HTTP 403 (otherwise the API is open)". Per-org `package_count` is null. "`package_search?rows=1000` returns up to 1000 records — paginate with `start=`". It also says "no auth, no geo-restriction observed from .il, EU, US testing", and lists `datastore_search_sql` only "(where enabled)". [danielrosehill README](https://github.com/danielrosehill/Israel-Open-Data-Resources/blob/main/060526/README.md). Confidence: secondary.
- **File downloads fail.** In the 2026-10-09 build, every resource file download (053cea08, 851ecab1, 4e6b9724, ec8cbc34, 39f455bf, 2c33523f) returned "HTTP 302 from e.data.gov.il: redirect to a non-gov host accounts.google.com". The build fell back to `datastore_api`, paging 32,000 rows at a time at no more than 4 requests per second. [tripy manifest.json](https://github.com/giladscore494/tripy/blob/main/data/gov/manifest.json), [tripy ingest.py docstring](https://github.com/giladscore494/tripy/blob/main/src/gov_data/ingest.py). Confidence: secondary (observed by an automated client).
- **Estimated totals.** Large resources return an *estimated* `total` (`total_was_estimated: true`). Only the 3,628-row recall resource gave an exact total. tripy accepts an estimate when rows read are within 2%. [tripy report](https://github.com/giladscore494/tripy/blob/main/data/gov/report.md). Confidence: secondary.
- **Third-party claims on limits.** A third-party AI-skill page says rate limiting is "strict and undocumented", says rapid sequential requests get blocked, and attributes a 403 on SQL queries to `datastore_search_sql` being disabled. [skills.lc israel-gov-api](https://skills.lc/skills-il/government-services/skills-il-government-services-israel-gov-api-skill-md). Confidence: secondary, low quality.
- **Developer experience.** The israel_cars README warns "Be mindful of data.gov.il API rate limits" without giving numbers ([README](https://github.com/digitaloracle/israel_cars/blob/master/README.md)). MyCarPortal's 4-car comparison page needs 36 data.gov.il calls in about 5 seconds, "קרוב לגבול timeout" ([PROGRESS.md](https://github.com/DaelShloush/MyCarPortal/blob/main/docs/PROGRESS.md)). info4Car_bot uses a 5-second timeout per request ([base_provider.py](https://github.com/YoelTavger/info4Car_bot)). Confidence: secondary.
- **Official rate-limit documentation.** A web search found none. [search, 2026-11-25](https://api.data.gov/docs/developer-manual/) (results were for the US api.data.gov, which is not relevant). Result: not found.

### Inferences
- Querying live per page view is fragile, given the ~9 calls per report, estimated totals, undocumented throttling and slow responses. A competitor should mirror the datasets nightly through datastore paging, since the tables refresh daily at about 02:30 and the registry says data is current "until 09:00", and then serve lookups from its own database. (My estimate.)
- Paging about 4.2M rows at 32k rows per request is about 130 requests for the main registry alone. Across all resources, about 12–15M rows is feasible nightly at 4 requests per second. (My estimate.)

### Gaps
- No public downtime history, SLA or status page was found. Blocking behaviour (Imperva/WAF, User-Agent filtering) could not be verified because data.gov.il was unreachable from this sandbox.
- Whether `datastore_search_sql` is currently enabled: **contradiction / unverified**. tripy's code "tries" it; the third-party skill says it is disabled.

---

## 3. License terms per dataset, and data.gov.il terms of use

### Takeaway
Most vehicle datasets are licensed **"אחר (פתוח)" / "Other (Open)"** (`license_id: other-open`, `isopen: true`). The recall notices, safety-system, garages, dealers, assessors and parts-business datasets are **Creative Commons Attribution (cc-by)**. No vehicle dataset was found marked non-commercial. The data.gov.il general license reportedly allows commercial use, is perpetual and royalty-free, keeps an attribution condition, and is overridden by any dataset-specific license.

### Cited Findings
- **License by dataset** (from `license_id` / `license_title` in the [raw CKAN dump](https://github.com/danielrosehill/Israel-Open-Data-Resources/blob/main/060526/datasets-raw.json), 2026-05-06). Confidence: secondary.
  - **other-open, "אחר (פתוח)"**: private-and-commercial-vehicles, reshev_bitul_sofi, rechev_le_pail_with_degem, motorcycle, heavy-truck, kli_rechev_ciburiim, bus_fleet, personal_import_vehicles, degem-rechev-wltp, tozeret, hagbalat_recall, mehir_yevuan, vehicles_filters_reduce_emissions, hatkana_nekudat_igun, rechavim_hashmalim.
  - **other-open, written in English "Other (Open)"**: shinui_mivne (history and ownership).
  - **cc-by, "Creative Commons Attribution"** (license_url `http://www.opendefinition.org/licenses/cc-by`): recall (2c33523f), zakaut-hatkana (83bfb278), musachim, socharim, shamaim_rechev, batei-esek.
- **Licence strings seen live on 2026-10-09.** tripy read "Other (Open)" for mehir_yevuan and "Creative Commons Attribution" for recall. [tripy DATA_SOURCES.md](https://github.com/giladscore494/tripy/blob/main/DATA_SOURCES.md). Confidence: secondary (live CKAN read).
- **data.gov.il terms of use** ([https://data.gov.il/he/terms-of-use](https://data.gov.il/he/terms-of-use)). **I could not fetch the page**, so I cannot give the exact quote that was requested. The search summary of the page, which is secondary and paraphrased, says:
  - use of the site is subject to the gov.il terms;
  - a license attached to a specific dataset overrides the general license;
  - the general license is "worldwide, royalty-free, unlimited-term, non-exclusive" and "commercial use is expressly permitted";
  - a breach ends the license immediately, and conditions that by nature continue, "including attribution", survive;
  - the ministry may change the license at any time, effective on posting.

  Source: [WebSearch summary of data.gov.il/he/terms-of-use](https://data.gov.il/he/terms-of-use). Confidence: secondary. **Exact Hebrew wording of the commercial-use and attribution clauses: not obtained.**
- **tripy's reading of the terms.** "data.gov.il terms permit copying, storage, processing, derived works, commercial use and public display, with the source metadata kept and no misleading presentation or privacy harm." [tripy DATA_SOURCES.md](https://github.com/giladscore494/tripy/blob/main/DATA_SOURCES.md). Confidence: secondary paraphrase.
- **tripy's attribution template.** "מקור: משרד התחבורה והבטיחות בדרכים, data.gov.il — {title_he} ({resource_id}), נכון ל-{date}", with "רישיון CC BY" appended for cc-by datasets. [tripy data/gov_datasets.json](https://github.com/giladscore494/tripy/blob/main/data/gov_datasets.json). Confidence: secondary (an example of practice).
- **Older context.** A 2016 inter-ministerial report describes a dedicated open-use license for data.gov.il that "restricts certain uses". [gov.il report 2016](https://www.gov.il/BlobFolder/policy/report_inter_ministerial_improve_access_to_public_databases/he/DataBaseAccessibilityReport290716a.pdf). Confidence: secondary, possibly outdated.
- **Contrast with other authorities.** The Survey of Israel (מפ"י) bars commercial use without written consent. The CBS license allows commercial use with attribution. [search summary](https://www.cbs.gov.il/he/Pages/%D7%A8%D7%99%D7%A9%D7%99%D7%95%D7%9F-%D7%A9%D7%99%D7%9E%D7%95%D7%A9.aspx). Neither is a vehicle source.

### Inferences
- Commercial reuse of all the vehicle datasets appears permitted. Attribution should be shown on every report: attribution survives termination under the general terms and is mandatory for cc-by. The safest practice is attribution plus "נכון לתאריך" on every page. (My estimate.)
- Because "Other (Open)" defers to the data.gov.il general terms, those terms (including the privacy and "no misleading presentation" clauses tripy paraphrases) govern most of the vehicle data. A lawyer should read the live terms text. (My estimate.)

### Gaps
- Verbatim Hebrew of the terms-of-use clauses on commercial use, attribution, disclaimer and changes. Not obtained because data.gov.il was blocked.
- The licences of rechev-tag-nachim (c8b9f9c8) and rechev_le_pail_without-degem (6f6acd03) were not confirmed from the raw dump.

---

## 4. Personal data, and whether ownership history linked to the plate is open

### Takeaway
Yes. Ownership history is published openly **per license plate** in bb2355dc and covers active private vehicles since 2017. It has only the **month of each ownership change and the ownership type**, with **no owner names, IDs or addresses**. No vehicle dataset found contains owner identity. Several datasets do contain quasi-identifiers linked to the plate, such as VIN, engine number and disability-tag status, which could count as personal data when combined with a known plate.

### Cited Findings
- **Ownership rows.** Fields are `mispar_rechev, baalut_dt, baalut` only. Example timeline: "02/2020–02/2022 פרטי; 02/2022–Present ליסינג". [israel_cars README](https://github.com/digitaloracle/israel_cars/blob/master/README.md), [MyCarPortal data-gov.ts OwnershipRecord](https://github.com/DaelShloush/MyCarPortal/blob/main/frontend/lib/api/data-gov.ts). Confidence: secondary.
- **Coverage.** The history datasets cover "כלי רכב פרטיים פעילים החל משנת 2017". [raw CKAN dump, shinui_mivne notes](https://github.com/danielrosehill/Israel-Open-Data-Resources/blob/main/060526/datasets-raw.json). Confidence: secondary (raw CKAN).
- **gov.il page.** A gov.il page titled "היסטוריית בעלויות של כלי רכב פרטיים" exists. Per the search snippet, it describes two databases: detailed records, and the number of prior owners with ownership type ("מאגר 1 ומאגר 2"). The page was about 1,746 days old. [gov.il private_vehicle_hoard](https://www.gov.il/he/pages/private_vehicle_hoard). Confidence: secondary (snippet only; page unreachable).
- **Plate-linked quasi-identifiers:**
  - VIN/chassis (`misgeret`) in the active registry, scrapped, personal-import and heavy datasets;
  - engine number (`mispar_manoa`) in the scrapped and history datasets;
  - disabled-parking tag per plate (c8b9f9c8), which **reveals that the owner or a household member holds a disability permit**;
  - open-recall status (36bf1404);
  - current ownership type (`baalut`) in the active registry.

  Sources: [raw CKAN notes](https://github.com/danielrosehill/Israel-Open-Data-Resources/blob/main/060526/datasets-raw.json), [MyCarPortal](https://github.com/DaelShloush/MyCarPortal/blob/main/frontend/lib/api/data-gov.ts). Confidence: secondary.
- **What a cautious reuser avoids.** tripy deliberately stores no per-vehicle record (only model or model-year aggregates) and never reads the TELEPHONE/WEBSITE columns of the recall data. [tripy data/gov/README.md](https://github.com/giladscore494/tripy/blob/main/data/gov/README.md). Confidence: secondary (an example of cautious practice).

### Inferences
- Under Israel's Privacy Protection Law, which Amendment 13 tightened from August 2025, plate-linked data could be "information about an identifiable person", because the plate is linkable to the owner through other sources. The disability-tag flag is the most sensitive item because it relates to health. Showing it in a public consumer report carries more risk than showing the other fields. (My estimate; not legal advice.)

### Gaps
- No official MoT privacy statement covering these specific datasets was found.
- Whether gov.il's own ownership-history service shows more than the open data (for example the exact number of owners including dealers): not verified.

---

## 5. Data-quality issues

### Takeaway
Measured problems:
- placeholder and empty dates in the road-entry field;
- many scrapped records missing the model code;
- recall manufacturer codes that do not match registry codes, and free-text multi-model recall entries;
- one `degem_cd` mapping to several models in the price list;
- field names with spaces;
- file-level "last updated" timestamps that the ministry itself says not to trust.

### Cited Findings
- **Untrustworthy file timestamp.** The registry remark says "אין להתייחס בשלב זה לתאריך העדכון של הקובץ". [raw CKAN dump](https://github.com/danielrosehill/Israel-Open-Data-Resources/blob/main/060526/datasets-raw.json). Confidence: secondary (raw CKAN).
- **Road-entry date (`moed_aliya_lakvish`).**
  - In the active registry (053cea08) the format is "YYYY-M" (e.g. '2009-9'), and **240,113 of 4,187,011 rows (5.7%) are empty**.
  - In 851ecab1 (scrapped), 653,622 values are empty and 565,338 are the placeholder '9999', with the rest year-only.
  - In 4e6b9724, 595,518 are empty and 74,775 are '9999'. In ec8cbc34, 498,248 are empty.
  - `bitul_dt` parsed 100% (ISO dates).

  Source: [tripy report 2026-10-09](https://github.com/giladscore494/tripy/blob/main/data/gov/report.md). Confidence: secondary (measured).
- **Missing `degem_cd` in scrapped vehicles.** 14.56% missing in 851ecab1, 41.87% in 4e6b9724 and 69.87% in ec8cbc34. Manufacturer codes are zero-padded ('0588') in the older files and unpadded ('593') in the current one. [tripy report](https://github.com/giladscore494/tripy/blob/main/data/gov/report.md). Confidence: secondary.
- **Recall data.**
  - `TOZAR_CD` matched the registry `tozeret_cd` for 0 of 84 codes, so it cannot be used as a join key.
  - `DEGEM` is free text, often listing several models ("VITO,VIANO"; "I5 IX1 X1 X2 X5 X6 XM 5 7").
  - 941 (make, DEGEM) pairs could not be matched to catalogue models.
  - There are misspellings, e.g. "TUSCON".

  Source: [tripy report](https://github.com/giladscore494/tripy/blob/main/data/gov/report.md). Confidence: secondary.
- **Price list.** 698 keys of (tozeret_cd, degem_cd, shnat_yitzur) carry more than one `kinuy_mishari`; for example Audi 19/10/2007 maps to both A3 and Q7, priced 175,450–670,850. 891 keys have 2–3 distinct prices. The list has no trim and no price date. [tripy report](https://github.com/giladscore494/tripy/blob/main/data/gov/report.md). Confidence: secondary.
- **Field names and code values.** Disability-tag field names contain spaces ("MISPAR RECHEV"), and earlier docs that used SUG_TAG were wrong ([MyCarPortal data-gov.ts](https://github.com/DaelShloush/MyCarPortal/blob/main/frontend/lib/api/data-gov.ts)). MyCarPortal's API doc warns that real field names differ from guessed ones (`mispar_dlatot`, `CO2_WLTP`, …) ([API-REFERENCE.md](https://github.com/DaelShloush/MyCarPortal/blob/main/docs/API-REFERENCE.md)). A GitHub project advises checking the `fields` array with `limit=0` before use ([EdenMalka58/DataGovIL](https://github.com/EdenMalka58/DataGovIL)). Confidence: secondary.
- **Inconsistent continuation-resource sizes.** One mirror cites 4,135,444 rows for the continuation resource, while another site claims more than 5.8M vehicles. [WebSearch summary](https://www.over.org.il/versions/4240a562-00de-44fd-80d8-6ca3d3dce8c7). Result: contradiction, unverified.
- **History coverage gaps.** "Some vehicles may not have mileage or history records". [israel_cars README](https://github.com/digitaloracle/israel_cars/blob/master/README.md). Confidence: secondary.
- **Odometer source.** `kilometer_test_aharon` is a single value from the *last* test only, not a series. [MyCarPortal TechnicalRecord](https://github.com/DaelShloush/MyCarPortal/blob/main/frontend/lib/api/data-gov.ts). Confidence: secondary.

### Inferences
- Odometer-rollback detection is not possible from open data alone, because there is one reading per vehicle. A competitor would need its own daily snapshots to build a reading history over time. (My estimate.)
- Number of owners ("יד") is derived by counting bb2355dc rows. Conventions differ, for example whether dealer (סוחר) periods count, so results vary between sites. [info4Car_bot vehicle_service.py](https://github.com/YoelTavger/info4Car_bot). (My estimate.)

### Gaps
- No public schema-change log exists. Stack Overflow and Israeli dev forums yielded nothing specific within the search budget.

---

## 6. Official free government consumer services

### Takeaway
gov.il has a free plate lookup (reportedly "מידע לציבור על רכב") and a page on private-vehicle ownership history. Both are built on the same MoT data. Many free third-party sites (carissues, lohit, carlab, testor, find-car, rechevcheck, Car check) already resell or repackage the open data for free.

### Cited Findings
- **gov.il plate lookup.** A blog says the free MoT service on gov.il is "מידע לציבור על רכב": you enter the plate without dashes and get model year, make, model, colour, fuel and last test date. [b-safed.co.il](https://b-safed.co.il/%D7%90%D7%99%D7%9A-%D7%9C%D7%91%D7%93%D7%95%D7%A7-%D7%90%D7%AA-%D7%94%D7%94%D7%99%D7%A1%D7%98%D7%95%D7%A8%D7%99%D7%94-%D7%A9%D7%9C-%D7%A8%D7%9B%D7%91-%D7%9C%D7%A4%D7%99-%D7%9E%D7%A1%D7%A4%D7%A8-%D7%A8/). Confidence: secondary, low.
- **gov.il ownership-history page.** [gov.il/he/pages/private_vehicle_hoard](https://www.gov.il/he/pages/private_vehicle_hoard). Confidence: secondary (snippet).
- **Free third-party lookups** built on data.gov.il: [carissues.co.il](https://carissues.co.il/vehicle-lookup), [lohit.co.il](https://lohit.co.il/), [carlab.co.il](https://www.carlab.co.il/plate), [testor.co.il](https://www.testor.co.il/vehicle-check), [find-car.info](https://find-car.info/), [rechevcheck.com](https://rechevcheck.com/), [car-check-il](https://car-check-il.netlify.app/guides/car-check-data-sources/), [govil.ai](https://govil.ai/datasets/). Open-source bots and apps include [info4Car_bot](https://github.com/YoelTavger/info4Car_bot), [israel_cars](https://github.com/digitaloracle/israel_cars) and [MyCarPortal](https://github.com/DaelShloush/MyCarPortal). Confidence: secondary.

### Inferences
- The open data is a commodity. Differentiation from Carzone has to come from non-government data (accidents, liens, insurance claims, market price) or from history built by keeping one's own snapshots over time. (My estimate.)

### Gaps
- The exact current name, URL and output fields of the gov.il lookup service, and whether it is free, were not verified because gov.il was unreachable.
- Whether a paid official "דו"ח היסטוריית רכב" exists from רשות הרישוי: not found.
- Liens are held by רשם המשכונות (Ministry of Justice), which has a paid search. It was not researched here: no open dataset was found.
