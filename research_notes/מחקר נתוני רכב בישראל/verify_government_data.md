# Checking the Israeli government vehicle open data against primary sources (data.gov.il CKAN API, data.gov.il terms, CBS)

All checks were run on **2026-11-25**, roughly 13:50–14:10 UTC. They check `government_data.md`, which was written without network access.

Confidence labels used below:
- **VERIFIED** means I read it myself today from the primary source: the data.gov.il API or page, or a cbs.gov.il PDF.
- **SECONDARY** means a search snippet, the press, or a third party.
- **ESTIMATE** means my own inference.

What could and could not be reached:
- **data.gov.il API: reachable.** `curl` returned HTTP 200 with no auth and no special User-Agent.
- **cbs.gov.il PDFs: reachable** with curl.
- **www.gov.il: not reachable.** curl got a Cloudflare 403 "Sorry, you have been blocked" (Ray ID a60128587fc5d6c5) on every gov.il page I tried. WebFetch failed with `getaddrinfo ENOTFOUND www.gov.il`. Every gov.il claim below is therefore SECONDARY.
- **e.data.gov.il (the CSV file host): blocked** by this sandbox's proxy, not by the site.

## Q1. data.gov.il terms of use: verbatim clauses (commercial reuse, attribution, liability, per-dataset licence precedence)

### Takeaway
The live Hebrew terms are dated "תאריך עדכון: 30/08/2025" and are run by מערך הדיגיטל הלאומי. They:
- **expressly allow commercial use**;
- require attribution;
- say a licence attached to a specific dataset overrides the general licence;
- disclaim all liability ("as is");
- **ban privacy-harming use, including cross-referencing with other sources, and ban presenting the data as if it were identified state data about a person.**

I found no English version of the terms.

### Cited Findings
All findings in this section are VERIFIED and come from [data.gov.il/he/terms-of-use](https://www.data.gov.il/he/terms-of-use), fetched 2026-11-25 (`www.` and the bare domain return the same page).

**Header and operator**
- "תאריך פרסום: 01/01/2018 / תאריך עדכון: 30/08/2025".
- "אתר אינטרנט זה (להלן: האתר) מנוהל ומתוחזק על ידי מערך הדיגיטל הלאומי (להלן – המשרד)."
- This is new information. The earlier notes did not name the operator.

**Per-dataset licence precedence** (verbatim): "השימוש באתר כפוף לתנאי השימוש המופיעים באתר www.gov.il (להלן: תנאי השימוש). השימוש במאגרי המידע, כהגדרתם לעיל, אינו כפוף לתנאי השימוש, אלא לרישיון השימוש המובא להלן. ככל שלמאגר מידע מוצמד רישיון שימוש השונה מהרישיון המובא להלן, יגבר הרישיון המוצמד למאגר המידע. הנכם מוזמנים להשתמש במאגרי המידע בכל אופן בו אתם מוצאים לנכון, בכפוף לתנאי רישיון השימוש."
- **Correction to the earlier notes:** using the *data* is **not** governed by the gov.il terms. Only use of the *site* is.

**Changes to the licence**: "המשרד רשאי לשנות את תנאי רישיון זה בכל עת, כאשר כל שינוי כזה ייכנס לתוקף מידית עם הצגתו באתר. השימוש במידע יהיה בכפוף לתנאי הרישיון שהיו בתוקף בתאריך ובשעה בהם נלקח המידע מהאתר."

**Grant**: "רישיון זה מעניק לך רישיון עולמי, ללא תמלוגים, בלתי מוגבל בזמן ולא בלעדי לשימוש במידע בכפוף לתנאים שלהלן."

**Commercial reuse**: "אתה רשאי להעתיק את המידע, להפיץ אותו, להעמיד אותו לרשות לציבור, לשדר אותו, לבצע שינויים טכניים במידע וליצור ממנו יצירות נגזרות בכל מדיום או פורמט. אתה רשאי לעשות שימוש במידע באופן מסחרי ובאופן שאינו מסחרי."

**Prohibited uses**, quoted verbatim in full:
1. "להציג את המידע באופן מטעה ו/או באופן הגורם למצג שווא ו/או לשנות את המידע בדרך שתגרום לסילופו ו/או באופן הפוגע או העלול לפגוע בכבודו או בשמו של בעל זכויות היוצרים בו."
2. "לעשות שימוש במידע באופן המפר חוק או דין."
3. "לעשות שימוש שיביא לפגיעה בפרטיותו של אדם, לרבות על ידי הצלבת המידע עם מקורות מידע אחרים."
4. "להציג את המידע באופן הנותן את הרושם כאילו קיבלת מידע מזוהה, או שהייתה לך גישה למידע מזוהה, המוחזק בידי המדינה אודות אדם."

**Attribution**: "בשימוש במידע, עליך לציין את מקור המידע. יוער, כי אין צורך לציין את מקור המידע לפי סעיף זה אודות השימוש בנתונים שנשאבו מן המידע, כאשר השימוש בנתונים איננו שומר על המקוריות בבחירה ובסידור של הנתונים שבמקור."

**Scope exclusions** ("רישיון זה אינו חל על:"). The list includes:
- "נתונים על אישיותו של אדם, מעמדו האישי, צנעת אישותו, מצב בריאותו, מצבו הכלכלי … כמשמעם בחוק הגנת הפרטיות, התשמ"א – 1981";
- "זכויות שאינן זכות יוצרים … ולרבות זכויות לפי חוק הגנת הפרטיות".

**No endorsement**: "רישיון זה אינו מקנה לך זכות להשתמש במידע באופן היוצר מצג או מרמז על כל מעמד רשמי בשימוש זה או על כך שהמדינה מעניקה חסות או נותנת גושפנקא…"

**Liability**:
- "המידע מועמד לרשותך על פי רישיון זה "כמות שהוא" (as is), ללא כל מצג, ערבות או התחייבות אודות המידע…"
- "המדינה אינה נושאת באחריות לכל נזק שייגרם לך או לכל צד ג' כתוצאה ישירה או עקיפה מכל מעשה או מחדל הנוגעים לשימוש במידע."
- The list continues with errors or omissions, changes made by the user, and third-party claims.
- "המדינה אינה מבטיחה או מתחייבת להבטיח את המשך אספקת המידע או המשך אספקתו בפורמט מסוים. המדינה שומרת לעצמה את הזכות להוריד מידע מן האתר בכל עת."

**Breach**: "הפרת רישיון זה על ידך תביא לסיומו המיידי. תנאים שלפי טבעם ממשיכים להתקיים גם לאחר ביטול הרישיון ימשיכו לחול, לרבות תנאים אודות ציון מקור המידע ותנאים אודות מצגים והעדר אחריות."

**Official publications prevail**: "במידה ותתגלה סתירה או אי-התאמה בין המידע לבין מידע המופיע בפרסומים הרשמיים בכתב של מדינת ישראל, רק החומר בפרסומים הרשמיים כאמור ייחשב כנכון."

**Law and venue**: Israeli law; "בתי המשפט בירושלים הם בעלי הסמכות הבלעדית".

**English version**: **not found.**
- `https://www.data.gov.il/en/terms-of-use` redirected to `/he/en/terms-of-use` and returned 404.
- `https://data.gov.il/en/terms-of-use` returned 403 on a later attempt.

**CKAN licence vocabulary**: `license_list` maps `other-open` to "אחר (פתוח)" and `cc-by` to "Creative Commons Attribution". The list also has `other-nc` "אחר (לא מסחרי)", `cc-nc` and `other-closed`. [license_list](https://data.gov.il/api/3/action/license_list). VERIFIED.

### Inferences
- Commercial reuse is expressly allowed. For `other-open` datasets the data.gov.il licence above applies. For `cc-by` datasets, CC BY prevails under the precedence clause, and attribution is required either way. (ESTIMATE)
- **Risk for a "car report by plate" product.**
  - Prohibition (3) bans privacy harm, "including cross-referencing with other sources". Prohibition (4) bans presenting results as if the operator had accessed identified state data about a person.
  - Combining plate data with other sources (such as accident or lien data, or user-supplied owner details) is therefore exactly the pattern the licence singles out.
  - The licence also does not cover health data at all. That bears on the disability-tag dataset (Q4).
  - (ESTIMATE; this needs a lawyer.)
- The "not endorsed" and "no official status" clauses mean a site must not look like an official MoT report. (ESTIMATE)

### Gaps
- No English or official translation of the terms exists.
- The gov.il site terms (which govern use of the site, not the data) were not readable because gov.il was blocked.

## Q2. Per-dataset metadata (package_show) and schema/count (datastore_search)

### Takeaway
Every key Ministry of Transport (MoT) dataset is live:
- licence `other-open` ("Other (Open)"), except the recall notices and **the disability tag dataset, which are `cc-by`**;
- extras `Frequency: Day`, `Update: Automat`;
- `metadata_modified` dated today, 2026-11-25, between about 03:35 and 03:52 (timezone not stated, probably UTC). The disability tag dataset is the exception, dated 2026-11-24 23:30.

Exact row counts are now known for all of them, and several earlier figures are corrected.

### Cited Findings
Sources: `package_show?id=<slug>` and `datastore_search?resource_id=<id>&limit=1`. Exact counts come from `limit=0&total_estimation_threshold=` (empty), which returned `total_was_estimated:false`. All are on https://data.gov.il/api/3/action/ and were read 2026-11-25. All VERIFIED.

**Inventory**

| Dataset (slug), resource | License (package_show) | metadata_modified / resource last_modified | Exact rows (today) | Earlier notes said |
|---|---|---|---|---|
| private-and-commercial-vehicles / 053cea08 (active registry) | other-open, "Other (Open)" | pkg 2026-11-25T03:52:03; res 03:42:39; 880,423,681 B | **4,204,570** (an estimated 4,204,611 without exact counting) | 4,187,011 (Oct; superseded) |
| same / 0866573c ("המשך") | same | res 2026-11-25T03:41:34; 305,286,379 B | **4,204,570** (identical to 053cea08) | "contradiction", see below |
| shinui_mivne / 56063a99 (history 1) | other-open, "Other (Open)" | pkg 03:45:06; res 03:39:57 | **2,516,178** | not read |
| shinui_mivne / bb2355dc (history 2, ownership) | same | res 03:41:07 | **5,622,462** | not read |
| reshev_bitul_sofi / 851ecab1, 4e6b9724, ec8cbc34 | other-open | 851ecab1 res 03:40:20; 4e6b9724 lm 2021-11-01; ec8cbc34 lm 2023-05-02 | **1,237,256 / 670,293 / 499,791** | 1,218,960 / same / same |
| rechev_le_pail_with_degem / f6efe89a | other-open | 03:42:22 | **612,493** | not read |
| rechev_le_pail_without-degem / 6f6acd03 | **other-open** (confirmed) | 03:37:07 | **1,441,777** | licence was unconfirmed |
| personal_import_vehicles / 03adc637 | other-open | 03:40:56 | **27,466** | not read |
| degem-rechev-wltp / 142afde2 (also 5e87a7a1) | other-open | 03:42:49 | **102,664** | not read |
| recall / 2c33523f | **cc-by, "Creative Commons Attribution"** | 03:40:37 | **3,665** | 3,628 (Oct) |
| hagbalat_recall / 36bf1404 (open recalls per plate) | other-open | 03:40:51 | **124,879** | not read |
| mehir_yevuan / 39f455bf (importer price list) | other-open | 03:41:07 | **102,664** | 101,824 (Oct) |
| rechev-tag-nachim / c8b9f9c8 (disability tag) | **cc-by, "Creative Commons Attribution"** | pkg **2026-11-24T23:30:17** | **632,724** | **CORRECTION: earlier notes said other-open "per index"** |
| motorcycle / bf9df4e2 | other-open | 03:35:44 | **194,046** | not read |
| heavy-truck / cd3acc5c | other-open | 03:42:14 | **425,645** | not read |

**Licence label.** The active-registry licence title is now in English, "Other (Open)", where the earlier notes had the Hebrew "אחר (פתוח)". It is the same `license_id`.

**Registry remark, confirmed verbatim:** "הנתונים במאגר מתעדכנים ברמה יומית עד השעה 09:00 בבוקר. אין להתייחס בשלב זה לתאריך העדכון של הקובץ." (`remark` field).

**Other resource metadata seen in package_show:**
- `datastore_contains_all_records_of_source_file: true`;
- a quality `score` block (e.g. cells_completeness 95 for 053cea08);
- file URLs on `https://e.data.gov.il/dataset/<pkg>/resource/<id>/download/<id>.csv`.

**Field names (datastore `fields` arrays, verbatim)**
- **053cea08**: `mispar_rechev, tozeret_cd, sug_degem, tozeret_nm, degem_cd, degem_nm, ramat_gimur, ramat_eivzur_betihuty, kvutzat_zihum, shnat_yitzur, degem_manoa, mivchan_acharon_dt, tokef_dt, baalut, misgeret, tzeva_cd, tzeva_rechev, zmig_kidmi, zmig_ahori, sug_delek_nm, horaat_rishum, moed_aliya_lakvish, kinuy_mishari`.
  - **Correction:** there is **no `rank` field**.
  - In the sample row, `moed_aliya_lakvish` = "2008-11" (YYYY-M format, as the earlier notes said) and `baalut` = "פרטי".
- **0866573c**: `mispar_rechev, tozeret_cd, sug_degem, degem_cd, kod_omes_tzmig_kidmi, kod_omes_tzmig_ahori, kod_mehirut_tzmig_kidmi, kod_mehirut_tzmig_ahori, grira_nm`.
  - Its resource notes: "המאגר מציג את מספרי הרישוי המופיעים בקובץ מספרי רישוי של כלי רכב פרטיים ומסחריים עם השדות הנוספים הבאים: קוד תוצר, קוד דגם, סוג דגם, קוד עומס צמיג קדמי…"
  - **Contradiction resolved:** it is a 1:1 extension table on the same plates (same exact count), not a continuation of rows.
  - MyCarPortal's claim that it has `merkav, mishkal_kolel, gorrar` is **wrong**.
- **56063a99**: `mispar_rechev, mispar_manoa, kilometer_test_aharon, shinui_mivne_ind, gapam_ind, shnui_zeva_ind, shinui_zmig_ind, rishum_rishon_dt, mkoriut_nm`. The `_ind` flags are 0/1 integers, not Y/N. `rishum_rishon_dt` is an ISO date.
- **bb2355dc**: `mispar_rechev, baalut_dt, baalut`. Sample: `{mispar_rechev:14817, baalut_dt:202202, baalut:"פרטי"}`. `baalut_dt` is numeric YYYYMM. Confirmed.
- **851ecab1**: `mispar_rechev, tozeret_cd, tozeret_nm, degem_cd, degem_nm, sug_rechev_cd, sug_rechev_nm, moed_aliya_lakvish, bitul_dt, misgeret, tozar_manoa, degem_manoa, mispar_manoa, mishkal_kolel, ramat_gimur, ramat_eivzur_betihuty, kvutzat_zihum, shnat_yitzur, baalut, tzeva_rechev, zmig_kidmi, zmig_ahori, sug_delek_nm, horaat_rishum, kinuy_mishari`.
  - It includes `baalut`, which the CKAN notes do not list.
  - The sample `moed_aliya_lakvish` is year-only (2014).
- **f6efe89a**: the same schema as 053cea08.
- **6f6acd03**: `mispar_rechev, mispar_shilda, tkina_EU, shnat_yitzur, tozeret_cd, tozeret_nm, tozeret_eretz_nm, sug_delek_cd, sug_delek_nm, mishkal_kolel, degem_nm, mishkal_azmi, nefach_manoa, degem_manoa, hanaa_cd, hanaa_nm, mishkal_mitan_harama, horaat_rishum`.
- **03adc637**: `mispar_rechev, shilda, tozeret_cd, tozeret_nm, sug_rechev_cd, sug_rechev_nm, degem_nm, mishkal_kolel, shnat_yitzur, nefach_manoa, tozeret_eretz_nm, degem_manoa, mivchan_acharon_dt, tokef_dt, sug_yevu, moed_aliya_lakvish, sug_delek_nm`. Sample `sug_yevu` = "יבוא אישי-משומש".
- **142afde2**: 98 fields. They include:
  - all the ADAS `_ind` flags listed earlier, plus `nikud_betihut` and `madad_yarok`;
  - `CO2_WLTP, HC_WLTP, PM_WLTP, NOX_WLTP, CO_WLTP, CO2_WLTP_NEDC`;
  - the NEDC fields `kamut_CO2…`;
  - `kinuy_mishari`.
  - **Correction to the Q1 gap in the earlier notes:** a "green index" field **does exist** as `madad_yarok`, inside the WLTP dataset.
- **2c33523f**: `RECALL_ID, TOZAR_CD, TOZAR_TEUR, DEGEM, SHNAT_RECALL, BUILD_BEGIN_A, BUILD_END_A, SUG_RECALL, SUG_TAKALA, TEUR_TAKALA, OFEN_TIKUN, TKINA_EU, YEVUAN_TEUR, TELEPHONE, WEBSITE`. Confirmed.
- **36bf1404**: `MISPAR_RECHEV, RECALL_ID, SUG_RECALL, SUG_TAKALA, TEUR_TAKALA, TAARICH_PTICHA`. Confirmed.
- **39f455bf**: `semel_yevuan, shem_yevuan, sug_degem, tozeret_cd, tozeret_nm, degem_cd, degem_nm, shnat_yitzur, mehir, kinuy_mishari`. Sample: Renault Twingo 1996, `mehir` 54,950, importer קרסו מוטורס. Confirmed.
- **c8b9f9c8**: `"MISPAR RECHEV", "TAARICH HAFAKAT TAG", "SUG TAV"`. Names with spaces confirmed. Sample `{50096, 20230419, 1}`.
- **bf9df4e2** (motorcycles): includes `misgeret, mispar_manoa, baalut, mkoriut_nm, sug_rechev_EU_cd, hespek`.
- **cd3acc5c** (heavy): includes `mispar_shilda, mispar_manoa, kvutzat_sug_rechev, grira_nm, sranim`.

**Notes text confirmed verbatim:**
- shinui_mivne: "המאגרים מציגים נתונים אודות כלי רכב פרטיים פעילים החל משנת 2017."
- hagbalat_recall: "כל הרכבים שעברה מעל חצי שנה מאז שקיבלו מכתב מהיבואן על קריאה חוזרת ולא ביצעו את התיקון המבוקש."
- **Discrepancy:** the remark "לרכבים אלה לא ניתן לחדש את רישיון הרכב…", quoted in the earlier notes, was not in today's package notes. I did not check the other package fields for it.
- mehir_yevuan: "…מחירי דגמי כלי רכב חדשים מתעדכנים עם קבלת המידע מהיבואן. מחירי כלי הרכב של דגמים ממשיכים מתעדכנים פעם בשנה."

**Ministry of Transport organisation size**
- `package_search?fq=organization:ministry_of_transport&rows=1000` gives **207 datasets today** (the earlier notes said 180 in May 2026).
- Licence split: cc-by 109, other-open 82, notspecified 15, blank 1.
- No used-car price-list, ownership-transfer, lien or stolen-vehicle dataset appears among their titles.
- VERIFIED.

### Inferences
- The exact count of 102,664 for both 142afde2 (WLTP models) and 39f455bf (price list) is a striking coincidence. It suggests both are built on the same model-code × year catalogue. I did not investigate further. (ESTIMATE)
- Every record count went up since October 2026, so the tables are live and growing. (ESTIMATE)
- The daily refresh lands at about 03:35–03:52 in the `metadata_modified` clock. If that clock is UTC, this is about 05:35–05:52 Israel time. The earlier notes' "02:25–02:36" is superseded. (ESTIMATE on timezone.)

### Gaps
- The CKAN timestamps give no timezone.
- 5e87a7a1 (counts by model) was not counted.

## Q3. API behaviour: latency, rate limiting, errors, datastore_search_sql, file downloads

### Takeaway
I observed no rate limiting at all:
- 60 sequential calls took 29 s and all returned 200;
- 40 calls at concurrency 20 all returned 200;
- single calls took 0.3–1.2 s;
- `limit=100000` works.

`datastore_search_sql` is **enabled but partly blocked**. A plain `SELECT … LIMIT n` works. Any query with `WHERE` or `COUNT(*)` returned an HTML "שגיאה" page with HTTP 404, which is most likely an edge or WAF filter.

Direct CSV downloads failed. data.gov.il's download path returned a CloudFront 403, and e.data.gov.il was blocked by this sandbox, so it is untested.

### Cited Findings
All VERIFIED on 2026-11-25 from this sandbox, which egresses via a US proxy (CloudFront POP IAD89).

**Latency**
- `package_show` (13 calls): 0.29–0.58 s.
- `datastore_search limit=1` (15 resources): 0.35–0.76 s.
- Exact counts with `limit=0`: 0.39–1.18 s.
- `limit=32000` on 053cea08 at offset 1,000,000: 2.85 s and 18.3 MB.
- `limit=100000`: 5.76 s and 56.7 MB, returning 100,000 records.
- **Correction:** 32,000 is the *default* limit (the echoed `"limit": 32000` on a filtered query), not a hard maximum.

**Rate limiting**
- 60 back-to-back requests to bb2355dc: all 200, 29.1 s in total.
- 40 requests with `xargs -P 20` to 053cea08: all 200.
- No `Retry-After` header and no 429 seen.
- Response headers: `x-cache: Miss from cloudfront`, a `TS012a021d` cookie (a cookie naming pattern used by F5 BIG-IP ASM), and `cache-control: public, max-age=0`.
- Requests with no User-Agent, and with curl's default User-Agent, also returned 200.

**Filtered lookup works**: `datastore_search?resource_id=bb2355dc…&filters={"mispar_rechev":14817}` returned 1 record in about 0.6 s.

**datastore_search_sql**

| Query | Result |
|---|---|
| `SELECT * FROM "2c33523f-…" LIMIT 1` | 200, success, returns `_full_text` too |
| `SELECT "RECALL_ID" FROM "2c33523f-…" LIMIT 2` | 200 |
| `SELECT * … WHERE "RECALL_ID" = 11020` | 404 HTML error page |
| `SELECT COUNT(*) FROM "2c33523f-…"` | 404 HTML error page |
| `SELECT count(_id) …` | 404 HTML error page |
| `SELECT … FROM "bb2355dc-…" WHERE "mispar_rechev"=14817` | 404 HTML error page |

This resolves the earlier "contradiction / unverified". The endpoint is *enabled*, but practically limited to unfiltered selects from this vantage point.

**Other errors observed**
- `package_search` with an `fl=name,title` parameter returned the same HTML error page; without `fl` it returned 200 in 1.55 s.
- `https://data.gov.il/dataset/recall/resource/2c33523f…/download`: CloudFront 403 ("Error from cloudfront").
- `e.data.gov.il` (the URL in the `url` field) could not be tested, because this sandbox's proxy has no rule for that host. **I could neither confirm nor refute** the earlier October finding that it redirects to accounts.google.com.

### Inferences
- Live per-plate lookups are fast enough (about 0.4–0.8 s per resource). Nightly mirroring is also easy: about 43 pages of 100k rows for the active registry.
- The lack of a documented SLA, the WAF behaviour on SQL, and the "המדינה אינה מבטיחה… המשך אספקת המידע" clause still argue for keeping your own mirror. (ESTIMATE)
- The throttling reported by third parties was not reproduced at up to about 2–20 requests per second. It may apply at higher volumes or from other IPs. (ESTIMATE)

### Gaps
- Behaviour at sustained high volume, and from Israeli IPs, was not tested.
- No official rate-limit documentation exists: none was found on data.gov.il.

## Q4. Does any dataset contain owner-identifying data?

### Takeaway
No dataset field contains an owner's name, ID number, address or phone number. This is VERIFIED from the full field lists above. The datasets do contain plate-linked quasi-identifiers:
- VIN (`misgeret` / `shilda` / `mispar_shilda`);
- engine number (`mispar_manoa`);
- ownership type and month per period (bb2355dc);
- odometer at the last test;
- **disability-parking-tag status per plate** (c8b9f9c8, 632,724 rows).

### Cited Findings
- The ownership table has only `mispar_rechev, baalut_dt, baalut`. [datastore_search bb2355dc](https://data.gov.il/api/3/action/datastore_search?resource_id=bb2355dc-9ec7-4f06-9c3f-3344672171da&limit=1). VERIFIED.
- The disability-tag package notes: "מאגר זה מכיל את מספרי הרכבים המורשים לשאת תג חניה לנכה של משרד התחבורה." Licence cc-by. [package_show rechev-tag-nachim](https://data.gov.il/api/3/action/package_show?id=rechev-tag-nachim). VERIFIED.
- The only person-like contact data seen is the importer's TELEPHONE and WEBSITE in the recall notices. These are corporate details. [datastore_search 2c33523f](https://data.gov.il/api/3/action/datastore_search?resource_id=2c33523f-87aa-44ec-a736-edbb0a82975e&limit=1). VERIFIED.
- The data.gov.il licence "does not apply to" health data as defined in the Privacy Protection Law, and forbids privacy-harming cross-referencing. [terms](https://www.data.gov.il/he/terms-of-use). VERIFIED.

### Inferences
- The disability tag reveals health-related information about the owner or household. The licence carves health data out of its scope, and the dataset carries a cc-by tag. Displaying it per plate in a commercial report is the highest-risk field. (ESTIMATE, not legal advice.)

### Gaps
- No MoT privacy statement specific to these datasets was found.

## Q5. gov.il consumer services: plate lookup, ownership history, "דוח בעלות", מחירון העם

### Takeaway
I could not open www.gov.il (Cloudflare block and DNS failure), so everything in this section is SECONDARY, from search snippets. They indicate:
- gov.il hosts free public plate-search front-ends for the same open datasets, as "DynamicCollectors" pages, including "private_vehicle_history_1/2";
- "דוח בעלות על כלי רכב" is a **separate service only for current or past owners**, issued through the personal area after National Digital Identity login;
- "מחירון העם" was a MoT crowdsourced used-car price list launched in 2020–2021, and I found no 2025–2026 status and no open dataset for it.

### Cited Findings
- **History (2) on gov.il.** [gov.il DynamicCollectors private_vehicle_history_2](https://www.gov.il/he/departments/dynamiccollectors/private_vehicle_history_2) is titled "מאגר היסטוריית כלי רכב פרטיים (2): מספר בעלויות קודמות וסוג הבעלות". Per the snippet, you search by plate; it covers private vehicles active since 2017; ownership dates are shown by quarter, with ownership type; and for a first-hand car the road-entry date appears in the ownership-date column. SECONDARY.
- **History (1) on gov.il.** [gov.il private_vehicle_history_1](https://www.gov.il/he/departments/dynamiccollectors/private_vehicle_history_1) is titled "מאגר היסטוריית כלי רכב פרטיים (1): מידע מפורט על הרכב", covering mileage and structural, colour and tyre changes. SECONDARY.
- **Active registry on gov.il.** [gov.il dynamiccollectors/private-and-commercial-vehicles](https://www.gov.il/he/departments/dynamiccollectors/private-and-commercial-vehicles) is a gov.il front-end for the active registry. SECONDARY (title only).
- **Quarter vs month: contradiction.** The snippet says the gov.il UI shows ownership "by quarter", while the API's `baalut_dt` is YYYYMM (month). The UI may aggregate. Unverified.
- **"דוח בעלות על כלי רכב".** [gov.il/he/service/vehicle-ownership-report](https://www.gov.il/he/service/vehicle-ownership-report). Per the snippet: vehicle owners, current or past, get a report of the vehicles registered in their name. You log in via הזדהות לאומית and request it in the personal area under "Documents"; support is via MoT and 1299. Fee: not stated in the snippet. **It is not a public lookup of another person's car.** SECONDARY.
- **Related service.** A certificate that no vehicle is registered in your name: [gov.il lack-of-registration](https://www.gov.il/he/service/lack-of-registration). SECONDARY.
- **"מחירון העם".** Press coverage dates the announcement to October 2020 and public availability to May 2021. It was based on voluntary reports from parties to ownership transfers. Insurers and leasing companies kept using Levi Yitzhak. Calcalist later reported it was not updated for popular models. Sources: [Walla, May 2021](https://cars.walla.co.il/item/3437202), [Cartube](https://www.cartube.co.il/חדשות-רכב/המחירון-של-העם-מחירון-רכב-יד-2-של-משרד-התחבורה-יוצא-לדרך), [iCar](https://www.icar.co.il/חדשות_רכב/באלגן_מאורגן:_מחירון_משרד_התחבורה_יוצא_לדרך/), [Calcalist](https://www.calcalist.co.il/local_news/car/article/hyzrqfbny). SECONDARY.
- **No price-list dataset on data.gov.il.** The 207 MoT datasets include no used-car price-list dataset; the only price data is `mehir_yevuan`. VERIFIED (the absence was checked across the MoT org listing).

### Inferences
- The earlier notes' "מידע לציבור על רכב" is probably the gov.il DynamicCollectors plate search. It shows the same fields as the open data, so it is no richer than the API. (ESTIMATE)
- The only official route to owner-linked history is the owner-only ownership report. No public official service exposes owner identity. (ESTIMATE, based on the snippets.)

### Gaps
- None of the gov.il pages were readable, so I could not check exact output fields, fees, or whether מחירון העם is still live and at what URL. **www.gov.il must be allowed in the session network settings** (and passed through Cloudflare) to verify these.

## Q6. CBS motor-vehicle figures for 2025

### Takeaway
CBS media release 126/2026 (29 April 2026), "כלי רכב מנועיים בישראל בשנת 2025", gives these end-2025 figures:
- **4,348,275 motor vehicles** (+3.0%), of which **3,789,429 private** (+3.2%);
- 419,447 added and 291,582 removed;
- **702,156 ownership transfers in 2025 (16.1% of the fleet)**, of which 604,033 were private cars.

### Cited Findings
All from [CBS release 126/2026 PDF](https://www.cbs.gov.il/he/mediarelease/DocLib/2026/126/27_26_126b.pdf), VERIFIED and read 2026-11-25:
- "4,348,275 כלי רכב מנועיים בישראל (גידול של 3.0% לעומת שנת 2024), מתוכם 3,789,429 כלי רכב פרטיים (גידול של 3.2% בדומה לשנת 2024)."
- "419,447 כלי רכב נוספו ו-291,582 נגרעו ממצבת כלי הרכב הפעילים, כך שמספר כלי הרכב גדל ב-127,865."
- "16.1% מכלי הרכב במצבה עברו העברת בעלות בשנת 2025 (702,156 כלי רכב)."
- The ownership-transfer section (p. 15): "בשנת 2025, בוצעו 702,156 העברות בעלות על כלי רכב (16.1% מתוך סך כלי הרכב), מתוכם 604,033 כלי רכב פרטיים, 45,904 משאיות ו-42,594 אופנועים."
- Other 2025 figures in the release:
  - 216,265 electric vehicles (+32.9%), with EVs 18.4% of new private cars (25.4% in 2024);
  - 587,314 hybrids including plug-ins (+22.8%);
  - average age 7.8 years;
  - 88.7% of private cars privately owned, with leasing 6.7%, companies 3.6% and rental 1.1%;
  - among new private cars, 56.0% private and 29.0% leasing;
  - 427 vehicles per 1,000 residents.
- The release states the data are CBS processing of "קובץ הרכב שהתקבל ממשרד התחבורה". This is stated in the 2024 release, [130/2025](https://www.cbs.gov.il/he/mediarelease/DocLib/2025/130/27_25_130b.pdf).
- **2024 comparison** (VERIFIED): 4,220,410 vehicles and 3,671,022 private; 396,531 added and 277,498 removed.

**Contradictions**
- A search-engine summary attributes **4,370,695** motor vehicles at the end of 2025 to CBS's "נסועה בשנת 2025" release ([CBS page](https://www.cbs.gov.il/he/mediarelease/Pages/2026/%D7%A0%D7%A1%D7%95%D7%A2%D7%94-%D7%91%D7%A9%D7%A0%D7%AA-2025.aspx)). The page is JavaScript-rendered and its text could not be extracted. This is SECONDARY and conflicts with the 4,348,275 in the fleet release; it may use a different definition. Use 4,348,275.
- Maariv's "מעל 4.3 מיליון" is consistent with 4,348,275 ([Maariv](https://www.maariv.co.il/news/israel/article-1378411)). SECONDARY.

### Inferences
- About 700k ownership transfers a year, about 604k of them for private cars, is the natural market-size anchor for "check before you buy" reports. (ESTIMATE)
- The active-registry count of 4,204,570 (private and commercial vehicles up to 3.5 t, model years 1996/1998 onward) sits below CBS's 4.35M total. That fits, since CBS also counts motorcycles, heavy vehicles and older vehicles. (ESTIMATE)

### Gaps
- I did not extract the CBS 2025 Excel tables (for example transfers by vehicle age).
- The "נסועה" release number and PDF were not located.
