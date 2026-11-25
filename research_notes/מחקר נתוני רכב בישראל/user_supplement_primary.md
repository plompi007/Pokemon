# User-supplied primary-source supplement (captured 2026-11-25 ~15:56 IST)

Supplied by the user in chat: live captures from data.gov.il and carlistprice.mot.gov.il. Key points integrated into the report:

- Terms of use (https://www.data.gov.il/he/terms-of-use, updated 30/08/2025), verbatim: commercial use allowed; dataset-attached licence prevails; prohibited: misleading presentation, unlawful use, privacy harm incl. cross-referencing, implying access to identified state data; no endorsement; as-is; no continuity; terms in force at time of download apply.
- Attribution not required for data extracted where use does not preserve original selection/arrangement.
- Scope exclusions: licence does NOT apply to data on a person's health, economic status etc. as defined in Privacy Protection Law (item 1), nor to rights under the Privacy Law (item 5). Combined with PPA 2022 position ("בעלות על רכב" = economic status), ownership-history data may fall outside the licence grant. [my inference; lawyer needed]
- MoT licence facets (package_search): cc-by 109, other-open 82, notspecified 15; total 207.
- Core packages other-open, license_url null: private-and-commercial-vehicles, shinui_mivne, hagbalat_recall, degem-rechev-wltp. Contact bidata@mot.gov.il.
- Registry remark: "הנתונים במאגר מתעדכנים ברמה יומית עד השעה 09:00 בבוקר. אין להתייחס בשלב זה לתאריך העדכון של הקובץ."
- Ownership history (bb2355dc) excludes vehicles that had a previous plate number.
- hagbalat_recall remark: vehicles >6 months past recall letter without repair cannot renew licence or transfer ownership.
- datastore_search_sql: `SELECT 1` succeeds; real-resource queries untested in this capture.
- carlistprice.mot.gov.il ("מחירון העם") live: crowd-reported sales + MoT statistical model; "כל הזכויות במידע שמורות למשרד התחבורה"; reliance disclaimer. No open dataset/API found.
- Registry estimated total 4,204,611 (total_was_estimated true) vs 4,204,570 in earlier count.
