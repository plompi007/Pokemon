# Verification against primary sources: Israeli legal and privacy findings for a vehicle-report-by-plate service

**Not legal advice.** These notes check `legal_privacy.md` against primary sources. Items marked [LAWYER] need a written opinion from an Israeli privacy or consumer lawyer.

**Date checked for every item: 2026-11-25.** Confidence labels:
- **[V]** verified in a primary source: official gazette (Reshumot / Sefer HaChukim), Knesset document, government PDF, or regulator document
- **[V-old]** verified in a primary source, but the text is an older or enacted version, not the current consolidated text
- **[S]** secondary source only
- **[E]** my inference

**Access log (important for the report writer):**
- **WebFetch:** failed with "ENOTFOUND" for www.gov.il, www.nevo.co.il and www.carzone.co.il.
- **curl:** reached the hosts, but:
  - **Nevo:** returned 403 "כתובת IP חסומה" (IP blocked) for every page.
  - **gov.il HTML pages:** returned a Cloudflare 403.
  - **gov.il PDFs:** files under `www.gov.il/BlobFolder/...` **did download**.
  - **Carzone:** returned 429 "Vercel Security Checkpoint" (a JavaScript bot challenge).
  - **Yad2:** returned a "Radware Page" bot challenge for /terms, /terms-of-use and the home page.
  - **fs.knesset.gov.il:** worked.
  - **library.mevaker.gov.il (State Comptroller):** failed.
- **Retries:** I retried the blocked hosts once later in the session (more than 30 seconds later). They were still blocked.
- **Result:** everything marked [V] below comes from Knesset PDFs or gov.il BlobFolder PDFs. I could not read the Nevo consolidated texts.

**Key primary source used:** ספר החוקים 3287 (Sefer HaChukim, issue 3287), 14 August 2024, חוק הגנת הפרטיות (תיקון מס' 13), התשפ"ד-2024 (Privacy Protection Law, Amendment 13), pp. 1430 onward — [gov.il BlobFolder PDF](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf). Below this is called "SH 3287".

---

## Q1. Amendment 13: definition of "מידע אישי" (personal information), registration duty, DPO duty, and fine amounts

### Takeaway
The official text confirms the definitions. "מידע אישי" is any datum relating to an identified or identifiable person, and identifiability is judged by "reasonable effort", directly or indirectly. Registration is required for two kinds of database: databases whose main purpose is collecting personal information to pass it on as a business or for payment, holding data on more than 10,000 people; and public-body databases. A DPO must be appointed by four categories of body.

**New and important finding:** s.8א(ג) excludes from the registration and notification duties any database that contains *only* information published to the public, or made open to public inspection, under lawful authority. That may matter for a service built solely on Ministry of Transport (MoT) open data. Fines are set out in s.23כו and in the Third Schedule of the law.

### Cited Findings
- **Commencement [V]:** "תחילתו של חוק זה שנה מיום פרסומו" (this Law takes effect one year from publication), s.74(א). Publication was 14.8.2024, so the law took effect on 14.8.2025. — [SH 3287](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **Definition of personal information [V]:** "'מידע אישי' - נתון הנוגע לאדם מזוהה או לאדם הניתן לזיהוי; ... 'אדם הניתן לזיהוי' - מי שניתן לזהותו במאמץ סביר, במישרין או בעקיפין, ובכלל זה באמצעות פרט מזהה, כגון שם, מספר זהות, מזהה ביומטרי, נתוני מיקום, מזהה מקוון, או נתון אחד או יותר הנוגע למצבו הפיזי, הבריאותי, הכלכלי, החברתי או התרבותי". In short: personal information is any datum about an identified or identifiable person, and a person is identifiable if they can be identified with reasonable effort, directly or indirectly, including through one or more data on their physical, health, **economic**, social or cultural situation. The list is illustrative ("כגון", "such as"), so the earlier note was correct. — [SH 3287, s.3 amendment to s.7](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **Definition of a database [V]:** "'מאגר מידע' - אוסף פרטי מידע אישי המעובד באמצעי דיגיטלי" (a collection of personal-information items processed by digital means). Two exclusions: a collection for personal, non-business use; and a collection of only name, address and contact details for 100,000 people or fewer that reveals nothing more, provided the owner has no other collection on the same people. — [SH 3287](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **Registration duty, s.8א(א)(1) [V]:** a database must be registered if either:
  - "(א) מטרתו העיקרית היא איסוף מידע אישי לשם מסירתו לאחר כדרך עיסוק או בתמורה, לרבות שירותי דיוור ישיר, ויש במאגר מידע אישי על יותר מ־10,000 בני אדם" (its main purpose is collecting personal information to pass to another as a business or for payment, including direct-mail services, and it holds personal information on more than 10,000 people); or
  - "(ב) בעל השליטה במאגר המידע הוא גוף ציבורי" (the controller is a public body), unless it holds only employee data.

  Processing personal information in a database that must be registered but is not registered is prohibited (s.8א(א)(2)). — [SH 3287, p.1433](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **Notification duty, s.8א(ב) [V]:** a database that does not have to be registered, but holds "מידע בעל רגישות מיוחדת" (information of special sensitivity) on more than 100,000 people, must be notified to the Privacy Protection Authority (PPA) within 30 days. — [SH 3287](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **Exclusion for publicly released information, s.8א(ג) [V]:** "הוראות סעיף זה לא יחולו על מאגר שאין בו אלא מידע שפורסם לרבים על פי סמכות כדין או שהועמד לעיון הרבים על פי סמכות כדין" (this section does not apply to a database that contains only information published to the public, or made open to public inspection, under lawful authority). — [SH 3287, p.1434](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf). The same wording also appears in the Knesset consolidated draft of 21.7.24 — [Knesset PDF](https://fs.knesset.gov.il/25/law/25_ls_bk_4704176.pdf)
- **A parallel rule for public bodies, s.23ב [V; consolidated draft]:** a public body (such as the MoT) may not hand over personal information unless it was "פורסם לרבים על פי סמכות כדין, או הועמד לעיון הרבים על פי סמכות כדין" (published or opened to the public under lawful authority), or the data subject consented. — [Knesset consolidated draft 21.7.24](https://fs.knesset.gov.il/25/law/25_ls_bk_4704176.pdf)
- **DPO duty, s.17ב1(א) [V]:** four categories must appoint a "ממונה על הגנת הפרטיות" (privacy protection officer):
  1. a controller or holder of a public-body database (except security bodies);
  2. "בעל שליטה במאגר מידע שמטרתו העיקרית היא איסוף מידע אישי לשם מסירתו לאחר כדרך עיסוק או בתמורה... ויש במאגר מידע אישי על יותר מ־10,000 בני אדם" (the controller of a database whose main purpose is collecting personal information to pass on as a business or for payment, holding data on more than 10,000 people);
  3. a controller or holder whose core activities need "ניטור שוטף ושיטתי של בני אדם, ובכלל זה מעקב ... אחר התנהגותו, מיקומו או פעולותיו של אדם, בהיקף ניכר" (regular and systematic monitoring of people on a significant scale, including tracking their behaviour, location or actions). Mobile operators and online search providers are named as examples;
  4. a body whose main activity includes processing special-sensitivity information on a significant scale. Banks, insurers, general hospitals and health funds are named as examples.

  "Significant scale" is judged by factors listed in s.17ב1(ב): number of people, share of a population, volume and range of data, duration and frequency of processing, retention period and geographic reach. **This settles the "four or five categories" contradiction in the earlier notes: there are four.** — [SH 3287, pp.1437–1438](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **Statutory damages, s.15א [V]:** "פיצויים לדוגמה" (exemplary damages, awarded without proof of harm) "בסכום שלא יעלה על 10,000 שקלים חדשים" (not exceeding NIS 10,000) per violation. They are available for listed breaches, and several require a prior demand by the data subject. Examples:
  - processing in an unregistered database that must be registered, if the data subject asked for registration and 90 days passed;
  - collecting data without the s.11 notice, if the data subject asked and 30 days passed;
  - refusing an access request under ss.13/13א;
  - failing to correct, or to notify a refusal to correct.

  — [SH 3287, pp.1435–1436](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **Administrative fines, s.23כו [V]:**
  - **Registration failures, (א):** NIS 150,000, doubled if the database holds data on 1,000,000+ people. Covers processing in a database that must be registered but is not, false details in a registration application, failure to report changes, and failure to give the s.8א(ב) notice.
  - **Access and correction failures, (ב):** NIS 15,000.
  - **Notice and direct-mail failures toward individuals, (ג):** NIS 50 × the number of people approached (NIS 100 for special-sensitivity data), with a NIS 30,000 floor. Covers no s.11 notice, and direct mail in breach of s.17ו(א).
  - **Per-person fines, (ד):** NIS 2 per person in the database (NIS 4 for special-sensitivity data), with a NIS 20,000 floor (NIS 40,000 for special-sensitivity data). Covers notice failures toward an unspecified group, **failure to appoint a DPO under s.17ב1(א)(1) or (2)**, and failure to appoint a data-security officer.
  - **Unlawful processing and breach of orders, (ה):** NIS 4 per person (NIS 8 for special-sensitivity data), with a NIS 200,000 floor.
  - **Failure to hand documents to an inspector, (ז):** NIS 300,000.
  - **Data Security Regulations breaches, (ח):** amounts set in the Third Schedule according to security level, doubled for a high-level database holding data on 1,000,000+ people.

  — [SH 3287, pp.1453–1458](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **Third Schedule examples [V]:**
  - Item (1), failure to prepare the database-definitions document: NIS 2,000 (individual-run database) / 2,000 (basic level) / 40,000 (medium level) / 160,000 (high level).
  - Items (9) risk survey, (10) penetration tests, (21) reporting a security incident to the PPA and (24) oversight of an outside processor: up to **NIS 320,000** at high level.

  So the TAU clinic figure of NIS 320,000 is confirmed as the top Third Schedule amount, and NIS 640,000 is that amount doubled for 1M+ people. — [SH 3287, pp.1474ff](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **Fine reductions [V]:**
  - **Small businesses:** fines are capped for a "עסק זעיר" (micro business, turnover up to NIS 4M) and a "עסק קטן" (small business, NIS 4M–10M). The caps are NIS 20k / 40k, 50k / 100k, or 70k / 140k depending on the type of breach.
  - **Turnover cap:** on the violator's request, the fine is cut to **5% of annual turnover** if it exceeds that.
  - **Total:** cumulative reductions are capped at 70%.
  - **DPO reduction:** a 10% reduction for appointing a DPO applies **only** to bodies obliged under s.17ב1(א)(3) and (4). That confirms the earlier note that it does not help a data trader under (א)(2).

  — [SH 3287, Fourth/later schedule, pp.1487–1488](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **"NIS 3.2 million" figure:** not found in SH 3287. Treat it as unsupported. — [SH 3287](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **Transition rule [V]:** a database registered before the start date stays registered even if s.8א no longer requires it (s.76(א)). — [SH 3287](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)

### Inferences
- [E][LAWYER] **Is a plate-report seller a "data trader" (s.8א(א)(1)(א) / s.17ב1(א)(2))?** Selling per-plate reports fits "איסוף מידע אישי לשם מסירתו לאחר ... בתמורה" (collecting personal information to pass it on for payment) *if* the report content is personal information about owners. Holding data on more than 10,000 people is near-certain at national scale. If the business qualifies:
  - registration is required;
  - a DPO must be appointed (non-appointment fine: NIS 2 per person, minimum NIS 20,000);
  - no 10% DPO reduction is available.
- [E][LAWYER] **The s.8א(ג) exclusion is the strongest argument against registration.** It applies only if the database holds *nothing but* information the MoT published under lawful authority. Two things would probably take the database outside the exclusion:
  - adding any non-public source (insurer claims, mileage from garages, user accounts);
  - storing purchaser logs (who looked up which plate). Customer data is a separate database in any case.

  The exclusion covers only s.8א, that is, registration and notice. It does **not** remove the DPO duty under s.17ב1, the data-security duties, purpose limitation or the s.11 notice duty.
- [E] The "economic situation" limb of the identifiability definition, together with the PPA's view that vehicle ownership is economic-status information (see Q2), makes it hard to argue that ownership history for a privately owned car is not personal information.

### Gaps
- The full Third Schedule table was not transcribed. Only the sample rows above were read.
- The current Nevo consolidated text (with any post-2024 amendments) could not be read because Nevo blocks the IP.
- I found no PPA guidance interpreting s.8א(ג) for reuse of government open data.

---

## Q2. PPA guidance on licence plates and vehicle data; instruction 4/2012; Data Security Regulations 2017 levels

### Takeaway
A PPA position paper dated 20.12.2022, hosted on the Knesset site, lists "**בעלות על רכב**" (vehicle ownership) as an example of information about a person's economic situation, citing ע"א 86/89 מדינת ישראל נ' בנק הפועלים (State of Israel v. Bank Hapoalim), פ"ד מד(2) 726 (1990). That is very likely the "licence plates" Supreme Court ruling the Library of Congress summary mentioned. The same paper quotes Registrar instruction 4/2012 (cameras): footage is a database even when the people are unknown, because cross-matching can identify them. Amendment 13's Third Schedule restates the three security levels.

### Cited Findings
- **The paper [V]:** "גילוי דעת: מהם 'מידע' ו'ידיעה על ענייניו הפרטיים של אדם' בחוק הגנת הפרטיות" (Position paper: what are "information" and "knowledge about a person's private affairs" under the Privacy Protection Law), dated כ"ו כסלו תשפ"ג / 20.12.2022. — [Knesset-hosted PDF](https://fs.knesset.gov.il/25/law/25_ls_bk_3674622.pdf)
  - It lists, under "מצבו הכלכלי" (economic situation): "נכסיו של אדם... מקרקעין שברשותו, **בעלות על רכב**, ירושה, צו עיקול..." (a person's assets ... real estate he owns, **vehicle ownership**, inheritance, attachment orders ...). Footnote 35 cites "ע"א 86/89 מדינת ישראל נ' בנק הפועלים, פ"ד מד(2) 726 (1990)".
  - The paper is pre-Amendment 13. Its quotation of the law's own wording is [V-old]. That it is the PPA's paper is [V]: it refers to "גילוי הדעת של הרשות להגנת הפרטיות" (the PPA's position paper). The point it makes is [V].
- **Identifiability by reasonable means [V]:** the same paper says that information presented anonymously is identifying if it can be linked to a person "באמצעים כלשהם... על דרך ביצועה של 'הנדסה חוזרת'" (by any means ... by "reverse engineering"), citing ע"א 1697/11 גוטסמן נ' ורדי (Gottesman v. Vardi). It adds that an identifying datum that serves as a "מפתח" (key) to information about a person is itself information. — [Knesset-hosted PDF](https://fs.knesset.gov.il/25/law/25_ls_bk_3674622.pdf)
- **Instruction 4/2012 [V, as quoted by the PPA paper]:** הנחיית רשם מאגרי המידע 4/2012 "שימוש במצלמות אבטחה ומעקב ובמאגרי התמונות הנקלטות בהן" (Registrar's instruction 4/2012, use of security and surveillance cameras and the image databases they collect), para. 2.7. Surveillance cameras in public space, and the footage stored, "מהווים מאגר מידע, גם אם זהותם של האנשים המופיעים בצילומים אינה ידועה לבעל המצלמה" (are a database even if the camera owner does not know who appears in the footage), because of the possibility of cross-matching with other databases. The quoted part does **not** mention plate recognition. The earlier note's claim that 4/2012 specifically treats plate-recognition systems as databases remains [S] (Shomrim only). — [Knesset-hosted PDF](https://fs.knesset.gov.il/25/law/25_ls_bk_3674622.pdf)
- **Security levels as restated in Amendment 13's Third Schedule [V]** (definitions used for the fine table):
  - **Basic level:** among other conditions, the database's main purpose is *not* collecting data to pass on as a business, and the controller is not a public body.
  - **Medium level:** not individual-run and not high, and either (1) "מטרתו העיקרית היא איסוף מידע לצורך מסירתו לאחר כדרך עיסוק או בתמורה" (main purpose is collecting data to pass to another as a business or for payment), (2) a public body, or (3) holds special-sensitivity data.
  - **High level:** "(1) מאגר מידע כאמור בפרט (1) להגדרה 'מאגר שחלה עליו רמת האבטחה הבינונית' או מאגר מידע שיש בו מידע בעל רגישות מיוחדת שמספר בעלי ההרשאה... עולה על 100 או שיש בו מידע אישי על אודות 100,000 בני אדם ומעלה; (2) ... מזהים ביומטריים של 100,000 בני אדם ומעלה" (in short: a medium-level "data trade" database, or a special-sensitivity database with more than 100 authorized users or data on 100,000+ people, or a database of biometric identifiers on 100,000+ people).
  - "תקנות אבטחת מידע" means the Privacy Protection (Data Security) Regulations 2017, ק"ת התשע"ז עמ' 1022.

  — [SH 3287, pp.1473–1474](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)
- **"Individual-run database" [V]:** excludes data-trade databases and databases holding data on 10,000+ people. — [SH 3287](https://www.gov.il/BlobFolder/legalinfo/standards_law/he/laws_standards-law_law3287.pdf)

### Inferences
- [E] Read naturally, high-level item (1) appears to make **every data-trade database high-level**, whatever its size. The qualifiers about more than 100 users or 100,000+ people seem to attach only to the special-sensitivity limb. An alternative reading attaches the 100,000+ qualifier to both limbs. Either way, a national plate-report service that counts as a data trader would be **high level**. Fines for missing risk surveys or penetration tests would then reach up to NIS 320,000 (NIS 640,000 at 1M+ people). [LAWYER]
- [E] The ע"א 86/89 citation, a 1990 Supreme Court case on vehicle ownership, probably resolves the earlier "Library of Congress / licence plates" contradiction. I did not read the judgment itself. Medium confidence.

### Gaps
- Not found: any PPA guidance, opinion or enforcement specifically on vehicle-history or plate-lookup services, or on commercial reuse of data.gov.il datasets. The PPA's gov.il pages returned 403. A search limited to gov.il found nothing.
- The full instruction 4/2012 text was not read, and in particular not any plate-recognition passage.
- The First Schedule of the 2017 Regulations was not read directly (Nevo blocked). I relied on the Amendment 13 restatement.
- The judgment in ע"א 86/89 itself was not read.

---

## Q3. Consumer Protection Law: s.14ג distance-sale cancellation and exceptions; ongoing transactions and auto-renewal

### Takeaway
The enacted 1998 text of s.14ג(ד)(3) excludes "מידע כהגדרתו בחוק המחשבים, התשנ"ה-1995" (information as defined in the Computers Law 1995) from the distance-sale cancellation right. The Cancellation Regulations 2010 contain the same exclusion (reg. 6, item 7). An instantly delivered vehicle report is a strong candidate for this exception, but I did not verify the current consolidated wording.

On ongoing transactions, the primary material I could read is the 2008 bill (Amendment 26). It proposed cancellation by phone, fax, email, oral notice at the place of business or registered mail, with charging to stop from the date the consumer names. I could not read the current s.13ד text or the auto-renewal rules in the official consolidated text.

### Cited Findings
- **Enacted s.14ג, Amendment 7, 1998 [V-old]:**
  - (ג): cancellation in writing within 14 days of receiving the goods or the disclosure document, whichever is later. For a service, 14 days from the transaction, provided cancellation comes at least 2 non-rest days before the service.
  - (ד): "הוראות סעיף זה לא יחולו על עסקת מכר מרחוק של - (1) טובין פסידים; (2) שירותי הארחה, נסיעה, חופש או בילוי, אם המועד שנקבע למתן השירות חל בתוך שבעה ימים... (3) **מידע כהגדרתו בחוק המחשבים, התשנ"ה-1995**; (4) טובין שיוצרו במיוחד בעבור הצרכן...; (5) טובין הניתנים להקלטה, לשעתוק או לשכפול, שהצרכן פתח את אריזתם המקורית" (this section does not apply to a distance sale of: (1) perishable goods; (2) lodging, travel, holiday or leisure services due within seven days; (3) **information as defined in the Computers Law 1995**; (4) goods made specially for the consumer; (5) recordable or copyable goods whose original packaging the consumer opened).

  — [Knesset, חוק הגנת הצרכן (תיקון מס' 7), התשנ"ח-1998](https://fs.knesset.gov.il/14/law/14_lsr_211534.PDF). Later amendments changed the cancellation fee, the 4-month rule for some groups and other details. I could not read the current text.
- **Cancellation Regulations 2010 [V]:** the Fair Trade Authority's brochure on תקנות הגנת הצרכן (ביטול עסקה), התשע"א-2010 (Consumer Protection (Cancellation of Transaction) Regulations 2010) lists cases where "זכות הביטול ... לא תחול" (the cancellation right does not apply). Item 7 is "מידע כאמור בחוק המחשבים" (information as in the Computers Law). The brochure also confirms:
  - **Cancellation fee:** 5% of the price or NIS 100, whichever is lower.
  - **Ending an ongoing transaction:** it must end within 3 business days of the cancellation notice, or within 6 days if the notice is sent by registered mail.

  — [gov.il brochure, Nov 2010](https://www.gov.il/BlobFolder/reports/deal_cancelation_2010/he/deal-cancellation-nov-2010.pdf). The Consumer Protection Authority's 2018 enforcement policy refers to the regulations' exceptions as "תקנה 6(א)" (reg. 6(a)) — [gov.il PDF](https://www.gov.il/BlobFolder/dynamiccollectorresultitem/cpfta_mem8/he/docs_cpfta_BitulIskaDrishotMeyuhadot.pdf)
- **Ongoing transactions, Amendment 26 bill, 2008 [V, bill text only]:** הצעת חוק הגנת הצרכן (תיקון מס' 26) (ביטול עסקה מתמשכת), התשס"ח-2008 (the 2008 bill on cancelling ongoing transactions) proposed that:
  - the consumer may cancel by notice "באחד מאלה: טלפון, פקסימיליה, דואר אלקטרוני, הודעה בעל־פה במקום העסק או דואר רשום" (by any of: phone, fax, email, oral notice at the place of business, or registered mail);
  - the trader must state on each invoice the end date and the address for cancellation;
  - the trader must publish the cancellation methods on its website;
  - charging must stop from the date the consumer specifies.

  — [Knesset bill PDF](https://fs.knesset.gov.il/17/law/17_ls1_566698.pdf)
- **Amendment 35, 2012 [V, existence only]:** added s.13ד1, on refunds of excess charges in ongoing transactions billed by standing order or credit card. The text came out garbled and was not used further. — [Knesset PDF](https://fs.knesset.gov.il//18/law/18_lsr_301330.pdf)
- **Fixed-term deals [S, search summary of a Supreme Court decision]:** for a fixed-term transaction (s.13א), the trader must give prior written notice of the end date within a "notice period" (about 60 days before the end). Extension requires conditions including explicit consent. — [search result citing Supreme Court ע"א 3849/20](https://supremedecisions.court.gov.il/Home/Download?path=HebrewVerdicts%2F20%2F490%2F038%2Fa14&fileName=20038490.A14&type=4). I did not read the judgment.

### Inferences
- [E][LAWYER] Section 14ג(ד)(3) and reg. 6 item 7 give a reasonable basis to argue that a digital report delivered instantly is "information" exempt from the 14-day cancellation right. Points to check:
  - **Definition:** the Computers Law definition of "מידע" (information) is recalled, not verified, as data, signs, concepts or instructions, excluding software, expressed in any way.
  - **Bundles:** a subscription or report bundle may be treated as a *service* or an *ongoing transaction*, not as "information".
  - **Disclosure:** the exception still requires the s.14ג(א) pre-contract disclosures.
  - **Policy:** a voluntary refund policy for reports not yet viewed lowers dispute risk.
- [E] For subscriptions:
  - allow cancellation through every channel listed above, plus online if the consumer signed up online (believed to have been added by a later amendment; not verified);
  - stop charging within 3 business days;
  - send notice before a fixed term ends;
  - do not auto-renew without fresh consent.

### Gaps
- Not read: the current consolidated s.14ג, s.13א–13ד and any 2023–2026 auto-renewal or call-recording amendments ("Amendment 70" remains unverified). Nevo was blocked, gov.il HTML returned 403, and the State Comptroller 2026 consumer report PDF failed to download.
- Not verified: whether the information exception still sits at s.14ג(ד)(3) in the current text.

---

## Q4. Communications Law s.30א (anti-spam): the existing-customer exception

### Takeaway
A Knesset Legal Department paper (2017) confirms the s.30א(ג) exception. No prior consent is needed if four conditions are all met:
1. the recipient gave their details during a purchase, or during negotiations for one;
2. the advertising concerns a product or service of a similar kind;
3. the advertiser told the recipient their details would be used for advertising;
4. the advertiser offered a way to refuse, and the recipient did not use it.

Damages are up to NIS 1,000 per message without proof of harm.

### Cited Findings
- **Basic prohibition [V]:** s.30א prohibits sending "דבר פרסומת באמצעות פקסימיליה, מערכת חיוג אוטומטי, הודעה אלקטרונית או הודעת מסר קצר, בלא קבלת הסכמה מפורשת מראש של הנמען, בכתב, לרבות בהודעה אלקטרונית או בשיחה מוקלטת" (an advertisement by fax, auto-dialer, electronic message or SMS without the recipient's prior express consent, in writing, including by electronic message or a recorded call). — [Knesset Legal Dept., "חקיקה למניעת הפצה של דואר זבל" (legislation to prevent spam), 10.5.2017, pp.4–5](https://fs.knesset.gov.il/globaldocs/MMM/63275fbe-180e-e711-80cc-00155d0206a2/2_63275fbe-180e-e711-80cc-00155d0206a2_11_10750.pdf)
- **Existing-customer exception [V, paraphrase in the Knesset paper]:** the sender is not liable without consent if:
  - "הנמען מסר את פרטיו למפרסם במהלך רכישה של מוצר או שירות או במהלך משא ומתן לרכישה כאמור, ודבר הפרסומת מתייחס למוצר או לשירות מסוג דומה" (the recipient gave the advertiser their details during a purchase of a product or service, or during negotiations for one, and the advertisement concerns a product or service of a similar kind);
  - "המפרסם הודיע לנמען שהפרטים שמסר ישמשו לצורך משלוח דבר פרסומת מטעמו" (the advertiser told the recipient the details would be used to send it advertising);
  - "המפרסם נתן לנמען הזדמנות להודיע לו כי הוא מסרב... והנמען לא עשה כן" (the advertiser gave the recipient a chance to refuse, and the recipient did not).

  Consent may be withdrawn "בכתב או בדרך שבה שוגר דבר הפרסומת, לפי בחירת הנמען" (in writing or by the same channel the advertisement was sent through, at the recipient's choice). — [same Knesset paper](https://fs.knesset.gov.il/globaldocs/MMM/63275fbe-180e-e711-80cc-00155d0206a2/2_63275fbe-180e-e711-80cc-00155d0206a2_11_10750.pdf)
- **Damages and scope [V]:** "בסכום שלא יעלה על 1,000 שקלים חדשים בשל כל דבר פרסומת" (not exceeding NIS 1,000 per advertisement), in a civil or class action. Under Amendment 63, whoever's business the content promotes is also treated as the sender. — [same Knesset paper](https://fs.knesset.gov.il/globaldocs/MMM/63275fbe-180e-e711-80cc-00155d0206a2/2_63275fbe-180e-e711-80cc-00155d0206a2_11_10750.pdf)
- **Case law [S]:** the Supreme Court in ע"א 534/17 described the exception as four cumulative conditions. The similarity test is applied strictly. — [Supreme Court ע"א 534/17 (search snippet; download failed)](https://supremedecisions.court.gov.il/Home/Download?path=HebrewVerdicts%2F17%2F340%2F005%2Fy10&fileName=17005340.Y10&type=2)

### Inferences
- [E] Once a buyer has purchased a report, follow-up emails offering further vehicle reports probably fit "similar kind", provided the notice and opt-out were given at checkout. Promoting unrelated products (insurance, financing) probably does not. Separate opt-in is safer. [LAWYER] for cross-selling partner products.

### Gaps
- The statutory text of s.30א was not read directly (Nevo blocked). This section relies on the Knesset paper's quotation and paraphrase.

---

## Q5. Accessibility: Service Accessibility Regulations reg. 35 and statutory damages

### Takeaway
The official consolidated regulations (gov.il) confirm the following:
- **Reg. 35:** defines "שירות אינטרנט" (internet service) and "תקן נגישות אינטרנט" (the internet accessibility standard), meaning IS 5568.
- **Reg. 35א(א):** requires accessibility adjustments at level **AA**.
- **Reg. 35א(ד):** a deviation is not a breach unless the operator was sent a notice demanding a fix and failed to fix it within a reasonable time, at most about 60 days. This confirms the "prior notice" point at the level of the regulation itself.
- **Reg. 35ה:** requires an accessibility statement.

The statutory-damages amount was **not found** in any primary source.

### Cited Findings
- **Reg. 35 definitions [V]:** "'שירות אינטרנט' – תכנים בכל תצורה... המוצגים למשתמש באמצעות אתרי אינטרנט, מסמכים או יישומים (אפליקציות), שנועדו לספק למשתמש שירות ציבורי או מידע על שירות" (content in any format ... shown to the user through websites, documents or apps, meant to give the user a public service or information about a service). "'תקן נגישות אינטרנט' – תקן ישראלי 5568" (the internet accessibility standard is Israeli Standard 5568). — [gov.il consolidated regulations PDF](https://www.gov.il/BlobFolder/guide/accommodating_service_providing_rules/he/sitedocs_service_acessibility_regulations.pdf)
- **Reg. 35א(א) [V]:** "חייב יספק התאמות נגישות בשירות אינטרנט... לפי תקן נגישות אינטרנט בהתאם לקווים המנחים הקבועים בו, ברמה AA" (an obligated party must make its internet service accessible ... according to the internet accessibility standard's guidelines, at level AA). — [same PDF](https://www.gov.il/BlobFolder/guide/accommodating_service_providing_rules/he/sitedocs_service_acessibility_regulations.pdf)
- **Reg. 35א(ד) [V]:** "לא יראו סטייה מעמידה בהוראות סימן זה כהפרה של הוראות הנגישות, אלא אם כן נשלחה לחייב הודעה הדורשת ממנו לתקנה והחייב לא תיקנה בתוך זמן סביר אך לא יאוחר מ-[60] ימים מיום קבלת ההודעה" (a deviation from this part is not treated as a breach unless the obligated party was sent a notice demanding a fix and did not fix it within a reasonable time, and no later than [60] days from receiving the notice). The operator must also provide alternative access in the meantime.
  - The PDF's digits are encoded oddly: years appear as "2113" for 2013, and the figure shows as "61". The figure is most likely 60 days. Re-check it.

  — [same PDF](https://www.gov.il/BlobFolder/guide/accommodating_service_providing_rules/he/sitedocs_service_acessibility_regulations.pdf)
- **Reg. 35ה [V]:** an accessibility statement must be placed prominently on the site and in any app. It must include the adjustments made, the accessibility coordinator's details if one is required, and contact details for reporting problems, including a demand under 35א(ד)(1). — [same PDF](https://www.gov.il/BlobFolder/guide/accommodating_service_providing_rules/he/sitedocs_service_acessibility_regulations.pdf)
- **Reg. 35ו [V]:** exemptions are available for technological platform limitations, granted by an accessibility consultant for up to 3 years and renewable. — [same PDF](https://www.gov.il/BlobFolder/guide/accommodating_service_providing_rules/he/sitedocs_service_acessibility_regulations.pdf)
- **Small-business exemption [V, draft only]:** the 2017 draft amendment would exempt an "עוסק פטור" (VAT-exempt dealer) or a business with average turnover of NIS 100,000 or less. — [Knesset committee draft 5.9.2017](https://fs.knesset.gov.il/20/Committees/20_cs_bg_390611.pdf)

### Inferences
- [E] A paid reporting service is clearly a "שירות אינטרנט" (internet service). Build to IS 5568 / WCAG AA and publish the 35ה statement with a contact channel. Respond to accessibility demands within 60 days. That is the reg. 35א(ד) safe harbour against a deviation becoming a breach.

### Gaps
- **Not found in a primary source:** the statutory-damages-without-proof amount under the Equal Rights for Persons with Disabilities Law 1998 for accessibility breaches. The "about NIS 50,000, index-linked" figure is still unverified. A search limited to gov.il and knesset.gov.il did not surface it.

---

## Q6. Carzone and Yad2 terms of use: anti-scraping and data-source clauses

### Takeaway
**Not found.** Both sites block automated access:
- **Carzone:** returned a Vercel Security Checkpoint (HTTP 429).
- **Yad2:** returned a Radware bot-verification page.

I could not read their terms. The blocking itself is evidence that both sites technically resist automated retrieval.

### Cited Findings
- `https://www.carzone.co.il/terms`, `/privacy` and `https://carzone.co.il/terms` returned HTTP 429 with the title "Vercel Security Checkpoint" on several attempts on 2026-11-25. — [Carzone terms](https://www.carzone.co.il/terms)
- `https://www.yad2.co.il/terms`, `/terms-of-use` and the home page returned HTTP 200 with the title "Radware Page" ("Verifying your browser before proceeding..."). — [Yad2 terms](https://www.yad2.co.il/terms)

### Inferences
- [E] Both sites deploy bot-mitigation. Scraping them would mean circumventing technical measures, which strengthens any contract or tort claim against a scraper. The earlier recommendation stands: do not scrape competitors.

### Gaps
- The actual anti-scraping and data-reuse clauses, and any statement by Carzone about its data sources (for example MoT or data.gov.il), still need a manual read in a normal browser.
