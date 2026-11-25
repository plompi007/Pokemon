# Israeli legal and privacy risk map: a commercial vehicle-report-by-plate service (competing with Carzone)

**This is not legal advice.** These are research notes. Before launch, get a written opinion from an Israeli privacy, consumer and IP lawyer. The items marked [LAWYER] need one in particular.

**Date checked for every item: 2026-11-25.** Confidence labels:
- **[V]** verified in primary source
- **[S]** secondary source (law firm, NGO or news summary seen in search results)
- **[E]** my estimate or recollection; not verified this session

**Method limitation (important):** WebFetch could not reach www.gov.il, alaw.co.il or other hosts from this session. The error was "host not in allowed network domains". So no page was opened and read in full. Every finding below comes from search-result snippets and summaries. Strictly, nothing here reaches the "[V]" level. Where a snippet quotes a primary document (Knesset, gov.il, Nevo), I mark it [S+] (secondary reading of a primary source). The report writer should treat [S+] as "probably right, re-check the text". To reach [V], allow www.gov.il, nevo.co.il and fs.knesset.gov.il in the session's network settings and re-run.

---

## Q1. Is a license plate, and data linked to it, "personal information" under the Privacy Protection Law, including after Amendment 13? Is there Privacy Protection Authority (PPA) guidance on plates, vehicle data or reusing open government data?

### Takeaway
After Amendment 13, "מידע אישי" (personal information) means any data relating to an identified or identifiable person, and identifiability is judged by "reasonable effort", directly or indirectly. A plate number that the Ministry of Transport (MoT) registry links to an owner is very likely personal information about that owner. That covers the ownership history, ownership type (private, company, leasing), number of owners and dates, and accident/claim data. The risk is highest when the vehicle is privately owned and the data is combined with other sources. I found no PPA opinion that deals specifically with selling plate-based vehicle reports or reusing data.gov.il vehicle datasets. The PPA does treat plate-recognition data as privacy-sensitive.

### Cited Findings
- Amendment 13 replaced the term "מידע" (information) with "מידע אישי" (personal information), defined broadly as "כל נתון הנוגע לאדם מזוהה או לאדם הניתן לזיהוי" (any data relating to an identified or identifiable person). An identifiable person is one who can be identified with reasonable effort, directly or indirectly, for example by name, ID number, biometric identifier, location data or online identifier. The list is illustrative ("כגון", "such as"). [S] — [y-law guide](https://www.y-law.co.il/blog/privacy-gdpr/privacy-act-13/); [Herzog Fox & Neeman, Amendment 13](https://herzoglaw.co.il/he/news-and-insights/%D7%AA%D7%99%D7%A7%D7%95%D7%9F-%D7%9E%D7%A1%D7%A4%D7%A8-13-%D7%9C%D7%97%D7%95%D7%A7-%D7%94%D7%92%D7%A0%D7%AA-%D7%94%D7%A4%D7%A8%D7%98%D7%99%D7%95%D7%AA/); [o-n.law](https://o-n.law/privacy-protection-law-amendment-no-13/); [mor.law](https://www.mor.law/data-privacy-israel-2025-amendment-13/)
- Data that does not identify anyone by itself, but can lead to identification when combined with other data, falls under the protection. [S] — same sources as above
- A Library of Congress summary of Israeli privacy law reports that Israel's Supreme Court held the definition of "information" in a database "should not be interpreted so narrowly as to exclude data such as those concerning automobile license plates". The summary attributes this to a 1990s decision and adds that the database need not be indexed by name. [S] — [Library of Congress, Online Privacy Law: Israel (mirror)](https://stuff.coffeecode.net/www.loc.gov/law/help/online-privacy-law/israel.php)
  - **Contradiction / unverified:** the leading Supreme Court case on what counts as a "database" is ע"א 439/88 רשם מאגרי מידע נ' ונטורה (Registrar of Databases v. Ventura), פ"ד מח(3) 808 (1994). The summaries I saw describe it as a database of dishonoured cheques, not plates ([Nevo](https://www.nevo.co.il/psika_html/elyon/PADI-NG-3-808-L.htm); [afiklaw](https://he.afiklaw.com/caselaw/5109)). That case held that the Registrar's power to refuse registration should be read broadly. I could not identify which ruling the LoC means by "license plates". The Knesset legal advisers' paper "מהם 'מידע' ו'ידיעה על ענייניו הפרטיים של אדם'" may cover it, but it was not read ([Knesset PDF](https://fs.knesset.gov.il/25/law/25_ls_bk_3674622.pdf)). Treat it as **not verified**.
- The PPA (and its predecessor ILITA) treats license-plate recognition as a privacy matter:
  - ILITA instruction 4/2012 treats video systems with plate recognition as databases under the law. [S] — [Shomrim](https://www.shomrim.news/eng/rosh-haayin-cancels-camera-fines)
  - The PPA has said local authorities cannot use LPR cameras for parking enforcement without explicit statutory authorization, and that LPR use "requires special and specific authorization". [S] — [Shomrim](https://www.shomrim.news/eng/rosh-haayin-cancels-camera-fines); [Shomrim on the court ruling](https://www.shomrim.news/eng/lpr-reports-without-authority)
- A July 2023 PPA opinion on employee vehicle-tracking and location data considered continuous location collection generally unjustified. This is relevant by analogy only. [S] — [DataGuidance](https://www.dataguidance.com/news/israel-ppa-publishes-opinion-collection-location-data)
- The PPA has said the law applies to information a system *infers* as well as to data fed into it. It has also published a data-minimisation paper (public consultation, March 2021). [S] — [ayr.co.il copy of the PPA paper](https://www.ayr.co.il/wp-content/uploads/2021/04/data_minimization_public_hearing.pdf)
- The MoT publishes the "מאגר היסטוריית כלי רכב פרטיים (2): מספר בעלויות קודמות וסוג הבעלות" dataset (private vehicle history: number of previous owners and ownership type) as a public lookup by plate number. It covers active private vehicles from 2017 on, with the dates of every ownership shown by quarter, and the ownership type. [S+] (seen in search snippets; the page could not be fetched) — [gov.il dataset 2](https://www.gov.il/he/departments/dynamiccollectors/private_vehicle_history_2); [gov.il dataset 1, detailed vehicle data](https://www.gov.il/he/Departments/DynamicCollectors/private_vehicle_history_1)
- Commercial sites state that the owner's name, ID and address are protected, and that no legitimate Israeli service returns them from a plate. They also say sites claiming to do so are probably using leaked databases. [S, low quality] — [freeland](https://freeland.co.il/%D7%90%D7%99%D7%AA%D7%95%D7%A8-%D7%91%D7%A2%D7%9C-%D7%A8%D7%9B%D7%91-%D7%9C%D7%A4%D7%99-%D7%9E%D7%A1%D7%A4%D7%A8-%D7%A8%D7%99%D7%A9%D7%95%D7%99/); [plateapp](https://plateapp.ai/owner); [cartube](https://www.cartube.co.il/איתור-מספר-רכב)

### Inferences
- [E] Plate plus ownership history (number of owners, dates, ownership type) is "information about an identifiable person" in the hands of anyone who can link the plate to the current or a past owner. Sellers and buyers usually can: a buyer knows who the seller is. So the "it's just car data" argument is weak, especially for privately owned cars. Company and leasing ownership is less sensitive, because corporations are not "persons" for privacy purposes. [LAWYER]
- [E] The fact that the government publishes the data as open data does not by itself remove the duties of a business that re-processes it: lawful processing, purpose limitation, notice and security. On the other hand, re-publishing exactly what the MoT itself publishes, without adding owner identities, is a defensible, lower-risk position. Adding accident, insurance-claim or odometer data from non-government sources, or combining sources, raises the risk.
- [E] Never display, infer or enrich owner identity (name, ID, phone, address). That is the clearest red line. Buying leaked or "data broker" owner data is a criminal and regulatory exposure.
- [E] Accident and insurance-claim history may come from insurers or the insurance claims registry. Those data flows are governed separately by insurance regulation and by contracts with the source. Check the legal basis for each source.

### Gaps
- Not found: any PPA guidance, opinion or enforcement action specifically on vehicle-history or plate-lookup commercial services, or on reusing data.gov.il data.
- Not verified: the Supreme Court "license plates" ruling cited by the LoC (case name and year unconfirmed).
- Not found: whether the MoT ran a privacy impact assessment or published a legal basis for releasing ownership-history counts and dates.

---

## Q2. What does Amendment 13 require (registration thresholds, notice duties, DPO, fines)? Which Data Security Regulations 2017 security level would apply?

### Takeaway
Amendment 13 took effect on 14 August 2025. Database registration now applies mainly to public-body databases and to databases whose main purpose is passing information to others for a living or for payment, holding data on 10,000+ people. A plate-report business may fall into that "selling information" category if the reports are personal information. That would make registration, a DPO and probably a medium or higher security level likely. Administrative fines are tiered and can reach hundreds of thousands of NIS per violation, capped at 5% of annual turnover. Statutory damages without proof of harm go up to NIS 10,000.

### Cited Findings
- Effective date: 14 August 2025. [S] — [Shachar law](https://shachar-law.co.il/%D7%AA%D7%99%D7%A7%D7%95%D7%9F-13-%D7%9C%D7%97%D7%95%D7%A7-%D7%94%D7%92%D7%A0%D7%AA-%D7%94%D7%A4%D7%A8%D7%98%D7%99%D7%95%D7%AA/); [ISOC-IL](https://www.isoc.org.il/regulation-digital-services/israel/israel-privacy-law-2024)
- Registration is limited to two categories:
  1. a public-body database;
  2. a database "שמטרתו העיקרית מסירת מידע לאחר כדרך עיסוק או בתמורה" (whose main purpose is passing information to another as a business or for payment) that holds data on 10,000+ people.

  A database not required to register that holds data of special sensitivity on more than 100,000 people must notify the PPA within 30 days. Databases registered before the amendment stay on the register until the controller notifies the PPA that the duty no longer applies. [S] — [Zemach Schneider & Co. (zes.co.il)](https://zes.co.il/%D7%AA%D7%99%D7%A7%D7%95%D7%9F-%D7%9E%D7%A1-13-%D7%9C%D7%97%D7%95%D7%A7-%D7%94%D7%92%D7%A0%D7%AA-%D7%94%D7%A4%D7%A8%D7%98%D7%99%D7%95%D7%AA/); [Shachar law](https://shachar-law.co.il/%D7%AA%D7%99%D7%A7%D7%95%D7%9F-13-%D7%9C%D7%97%D7%95%D7%A7-%D7%94%D7%92%D7%A0%D7%AA-%D7%94%D7%A4%D7%A8%D7%98%D7%99%D7%95%D7%AA/); [govextra.gov.il](https://govextra.gov.il/privacy-protection-regulations/privacy-protection-regulations/)
- The DPO (ממונה הגנת פרטיות) requirement applies to defined categories, including:
  - public bodies;
  - data traders (databases whose main purpose is passing information to others);
  - bodies whose core activity is systematic monitoring;
  - bodies processing sensitive data on a significant scale.

  Sources differ on whether there are four or five categories. [S; contradiction on the count] — [inplp](https://inplp.com/latest-news/article/new-amendment-to-israeli-privacy-protection-law-and-mandatory-dpo-appointment/); [melnik.org.il](https://www.melnik.org.il/en/israel-privacy-officer-amendment-13/); [Shachar law](https://shachar-law.co.il/%D7%AA%D7%99%D7%A7%D7%95%D7%9F-13-%D7%9C%D7%97%D7%95%D7%A7-%D7%94%D7%92%D7%A0%D7%AA-%D7%94%D7%A4%D7%A8%D7%98%D7%99%D7%95%D7%AA/)
- Fines (עיצומים כספיים) are tiered by violation type, database size and security level. A Tel Aviv University clinic table gives these figures:
  - up to NIS 320,000 for a high-security-level database;
  - NIS 640,000 for a database of more than 1 million people;
  - total sanctions capped at 5% of the violator's annual turnover.

  Other examples cited: NIS 150,000 for failing to register or notify a database; for breach of the notice duty, NIS 50 per data subject with a NIS 30,000 floor. A figure of "NIS 3.2 million" appears in a vendor guide. [S; amounts vary between sources: contradiction] — [TAU Law clinic, עיצומים table (PDF)](https://law.tau.ac.il/sites/law.tau.ac.il/files/media_server/law_heb/Clinics/privet/files/itzumim_privacy.pdf); [lilachbullock](https://www.lilachbullock.com/tikun-13-hagnat-hapratiut/); [peopleofinternet](https://peopleofinternet.com/articles/israel-s-amendment-13-converts-privacy-law-into-a-real-enfor.html)
- If a body that must appoint a DPO does so, and it is not a public body or a data trader, the PPA may cut other fines by 10%. Note that this reduction does **not** help a data trader. [S] — [peopleofinternet](https://peopleofinternet.com/articles/israel-s-amendment-13-converts-privacy-law-into-a-real-enfor.html)
- Statutory damages without proof of harm: up to NIS 10,000 (new s.15א, extended to breaches of chapters ב and ד). One source mentions up to NIS 50,000 in another context (s.29א). Breach of the notice duty and refusal of an access request are cited as grounds. [S] — [ISOC-IL](https://www.isoc.org.il/regulation-digital-services/israel/israel-privacy-law-2024); [niloosoft](https://www.niloosoft.com/%D7%AA%D7%99%D7%A7%D7%95%D7%9F-13-%D7%9C%D7%97%D7%95%D7%A7-%D7%94%D7%92%D7%A0%D7%AA-%D7%94%D7%A4%D7%A8%D7%98%D7%99%D7%95%D7%AA)
- Early enforcement: a fine of about NIS 256,000 on the Meuhedet health fund for not immediately reporting a serious security incident. The date is contradictory between sources. [S] — [peopleofinternet](https://peopleofinternet.com/articles/israel-s-amendment-13-converts-privacy-law-into-a-real-enfor.html)
- The Data Security Regulations 2017 (תקנות הגנת הפרטיות (אבטחת מידע), התשע"ז-2017):
  - in force since 8 May 2018;
  - three security levels (basic, medium, high);
  - medium and high levels require automatic access logging, with logs kept for at least 24 months.

  [S+] — [PPA guide on regulation 10 (gov.il PDF)](https://www.gov.il/BlobFolder/reports/takana10d/ar/takanat10d.pdf); [Calcalist](https://www.calcalist.co.il/articles/0,7340,L-3774430,00.html); [Gornitzky memo (PDF)](https://www.gornitzky.com/wp-content/uploads/2018/05/cyber-may17.pdf)
- [E — from recollection of the First Schedule; not verified this session] Under the regulations:
  - **Medium level:** a database whose main purpose is collecting data to pass to others as a business, including direct-mail services.
  - **High level:** a medium-level database holding data on 100,000+ people, or with more than 100 authorized access holders.

  A national plate-report service selling reports at scale would therefore likely be **high level** if its database counts as personal information. Verify against the regulations' First Schedule on Nevo. [LAWYER]

### Inferences
- [E] Key classification question [LAWYER]: is the business a database "whose main purpose is passing information to another for payment"? Selling reports per plate is literally that. If the reports hold personal information on 10,000+ people (owners of the cars covered), the business probably has to:
  1. register the database;
  2. appoint a DPO (no 10% fine reduction available);
  3. apply medium or high security (likely high at national scale);
  4. give notice under s.11 to its own users;
  5. respond to access and correction requests (ss.13–14), including from car owners.
- [E] To reduce exposure: hold only MoT open-data fields, avoid storing purchaser-to-plate logs longer than needed, and do not build owner profiles.

### Gaps
- The exact statutory fine table and DPO categories were not read in the official text (Reshumot/Nevo blocked).
- No PPA guidance found on whether a service reselling open government data is a "data trader".

---

## Q3. What does the MoT itself allow? Rules on displaying ownership history or identifying details?

### Takeaway
The MoT itself publishes, as an open lookup by plate, the number of previous owners, ownership dates by quarter and ownership type for private vehicles from 2017 on. It does **not** publish owner identities. The "דוח בעלות על כלי רכב" (vehicle ownership report) service, which presumably includes identity-level detail, is limited to current or past owners who log in with national government identification.

### Cited Findings
- Dataset (2) "מספר בעלויות קודמות וסוג הבעלות" (number of previous owners and ownership type) is a public lookup by plate. It covers active private vehicles from 2017 on, shows ownership dates by quarter and shows ownership type. [S+] — [gov.il private_vehicle_history_2](https://www.gov.il/he/departments/dynamiccollectors/private_vehicle_history_2)
- The "דוח בעלות על כלי רכב" service is meant for people who own a vehicle or owned one in the past. It requires login to the personal government area through the national identification system. [S+] — [gov.il vehicle-ownership-report](https://www.gov.il/he/service/vehicle-ownership-report)
- data.gov.il datasets are published under an open-use licence that allows reuse anywhere, royalty-free, including derivative works. The licence reportedly requires any tool, app or service using the data to clearly state the data source: site name, dataset name and last update date. [S] — [Government ICT standards PDF (gov.il)](https://www.gov.il/BlobFolder/policy/data_publication_standards_and_guidelines/he/Data%20publication%20%E2%80%93%20standards%20and%20guidlines.pdf); [OSM forum quoting data.gov.il FAQ/licence](https://community.openstreetmap.org/t/new-gov-data-source/61963)

### Inferences
- [E] Displaying exactly what the MoT exposes publicly (owner count, ownership type, quarter-level dates) is the safest baseline. Showing anything more granular, or anything from the identified-owner service, would go beyond what the state itself made public.
- [E] Comply with the attribution clause: source, dataset name and last-updated date on each report. Do not imply government endorsement.

### Gaps
- Not read: the full data.gov.il terms (https://data.gov.il/terms) and any dataset-specific restrictions, for example on bulk commercial use or caching.
- Not found: whether the MoT has a policy against commercial resale of the ownership-history dataset.

---

## Q4. Scraping or reusing competitors' content (Carzone, Yad2); database copyright; unjust enrichment

### Takeaway
In Israel, facts and data are not protected by copyright (Copyright Law 2007 s.5). A compilation is protected only for original selection or arrangement (s.4(b)). Unjust-enrichment claims for copying unprotected material need an "extra element" (יסוד נוסף) beyond copying. The bigger practical risks are breach of the site's terms of use, technical and contractual claims, and the copying of original text and images. I did not find Carzone's or Yad2's anti-scraping clauses, or a Yad2 scraping judgment.

### Cited Findings
- Copyright does not extend to "עובדה או נתון" (a fact or a datum) (s.5). Courts are wary of unjust enrichment being used as a bypass of copyright law. Discussed in מעריב נ' אול יו ניד (Maariv v. All You Need) and ת"א 5150-05-14 לייבדיאנאס נ' שחר (LiveDNS v. Shahar). [S] — [the7eye: Maariv v. All You Need](https://www.the7eye.org.il/verdicts/50152); [law.co.il: LiveDNS v. Shahar (PDF)](https://www.law.co.il/media/computer-law/livedns4.pdf)
- A database qualifies for originality only if the selection or arrangement is original (s.4(b)). בזק נ' דפי זהב (Bezeq v. Dapei Zahav) limited protection of databases. In סגל נ' גולדהמר (Segal v. Goldhammer), a compilation with no filtering, or with only one real arrangement option, is not protected, and copying alone is not enough for unjust-enrichment restitution. The court referred to the tests in the הסדר ההימורים (sports betting arrangement) case. [S] — [Drori Stav IP, database copyright (Supreme Court)](https://dwo.co.il/he/%D7%96%D7%9B%D7%95%D7%99%D7%95%D7%AA_%D7%99%D7%95%D7%A6%D7%A8%D7%99%D7%9D_%D7%91%D7%9E%D7%90%D7%92%D7%A8_%D7%A0%D7%AA%D7%95%D7%A0%D7%99%D7%9D/); [gsip](https://www.gsip.co.il/%D7%96%D7%9B%D7%95%D7%99%D7%95%D7%AA-%D7%99%D7%95%D7%A6%D7%A8%D7%99%D7%9D/%D7%9E%D7%90%D7%92%D7%A8%D7%99-%D7%9E%D7%99%D7%93%D7%A2/)
- Carzone terms page exists at carzone.co.il/terms. Its snippet covers scope, service description, changes and account suspension. **The scraping clause was not found.** Carzone also publishes a privacy policy and an order-cancellation policy. [S] — [Carzone terms](https://www.carzone.co.il/terms); [Carzone privacy](https://www.carzone.co.il/privacy); [Carzone cancellation](https://www.carzone.co.il/order-cancellation)
- Comparable Israeli car sites expressly prohibit automated retrieval and scraping (Mazda online shop terms) and copying beyond personal use (iCar). [S] — [Mazda terms (PDF)](https://mazda.co.il/מאזדה_אתר_הזמנות_אוןליין_תקנון_2209_G3693-V001.pdf); [iCar terms](https://www.icar.co.il/Terms/)

### Inferences
- [E] Copying Carzone's underlying MoT data is low copyright risk, because it is the same public facts. But copying its report text, layouts, photos, model reviews or proprietary data (for example price estimates) creates risk under copyright, terms-of-use contract, unjust enrichment and possibly unfair competition (חוק עוולות מסחריות, Commercial Torts Law). Build from primary government sources directly. Do not scrape competitors. [LAWYER]
- [E] Scraping Yad2 listings (prices, photos, sellers' phone numbers) adds a privacy problem: sellers' contact details are personal information. It also invites a terms-of-use claim. Avoid it.

### Gaps
- Not found: Carzone's and Yad2's actual anti-scraping clauses (WebFetch blocked).
- Not found: an Israeli judgment specifically on Yad2 scraping. I believe Yad2 has litigated against copying of listings, but could not confirm a case name. Not reported.

---

## Q5. Liability for wrong information that causes a user loss

### Takeaway
Israeli tort law recognizes negligent misrepresentation (מצג רשלני) where reliance is foreseeable. A paid report that buyers rely on to buy a car is exactly that kind of situation. Disclaimers help, but they are limited by the Standard Contracts Law and the Consumer Protection Law. I found no case on vehicle-history sites.

### Cited Findings
- The Supreme Court (planning context) held that there is a duty to give true and reliable information where reliance is foreseeable and likely, and that giving partial information that creates a false impression is negligence. [S] — [Bizportal summary](https://www.bizportal.co.il/general/news/article/168091)
- A claim against Bezeq failed on causation even though the court found a negligent, untrue statement. [S] — [Globes](https://www.globes.co.il/news/article.aspx?did=1000419530)
- Academic debate exists on whether reliance is required for misrepresentation. [S] — [TAU Law Review](https://www.taulawreview.sites.tau.ac.il/_files/ugd/e74fa2_a5bdaaf5476644eb90cc3a3a1b08cb76.pdf)

### Inferences
- [E] Mitigations:
  - State the source and "as of" date for each field.
  - Say clearly what the report does *not* cover (for example, accidents not reported to insurers, odometer not verified).
  - Recommend a mechanical inspection.
  - Cap liability at the report price, but note that an unreasonable exclusion in a standard consumer contract may be voided as a "תנאי מקפח" (unfair term) under the Standard Contracts Law 1982.
  - Do not market reports as "guaranteed" or "complete". Misleading claims are also a s.2 Consumer Protection Law issue.
  - Consider professional indemnity / E&O and cyber insurance.
  - [LAWYER] for the terms of use.

### Gaps
- Not found: Israeli case law on vehicle-history report errors or on enforceability of website disclaimers.

---

## Q6. Consumer protection: distance selling, cancellation, subscriptions and auto-renewal, disclosures, anti-spam

### Takeaway
- Distance selling (s.14ג): 14-day cancellation, with a cancellation fee capped at 5% or NIS 100, whichever is lower. There are exceptions, including information products. Whether an instantly delivered digital report is a cancellable "service" or an exempt "information product" needs a lawyer's view.
- Recurring subscriptions are "ongoing transactions" with their own cancellation and renewal rules.
- The Communications Law s.30א requires prior express consent for marketing messages, with damages of up to NIS 1,000 per message without proof of harm.

### Cited Findings
- s.14ג: cancellation within 14 days from receiving the product or the transaction-details document, whichever is later. Cancellation fee capped at 5% or NIS 100, whichever is lower. Refund within 14 days. The trader must accept cancellation orally, by registered mail, by email or by fax. [S] — [danieli-law](https://danieli-law.co.il/cancellation-of-a-distance-selling-transaction/); [emun.org](https://www.emun.org/cancellation-guide/cancellation-distant-sale/); [gov.il Consumer Protection Authority (snippet)](https://www.gov.il/he/pages/returns)
- Exceptions include perishable goods, "information products (computer software)", custom-made goods, and copyable media once the packaging is opened. [S] — [law-tip](https://www.law-tip.co.il/%D7%91%D7%99%D7%98%D7%95%D7%9C-%D7%A2%D7%A1%D7%A7%D7%AA-%D7%90%D7%95%D7%A0%D7%9C%D7%99%D7%99%D7%9F-14-%D7%99%D7%95%D7%9D/); [zehavi-law](https://www.zehavi-law.co.il/post/%D7%AA%D7%A0%D7%90%D7%99%D7%9D-%D7%9C%D7%91%D7%99%D7%98%D7%95%D7%9C-%D7%A2%D7%A1%D7%A7%D7%AA-%D7%9E%D7%9B%D7%A8-%D7%9E%D7%A8%D7%97%D7%95%D7%A7)
- An ongoing service bought by distance selling can be cancelled even after the service has started (per "Amendment 26"). One-off services: cancellation must come at least 2 business days before the service. [S; sources inconsistent on the day-counts] — [consumers.org.il](https://www.consumers.org.il/category/remote-purchase); [lawreviews](https://www.lawreviews.co.il/article/consumer-protection-law-israel-rights)
- Seniors (ותיקים), people with disabilities and new immigrants may cancel distance transactions within 4 months (Amendment 47). [S] — same sources
- A 2025 amendment ("Amendment 70" per one source) reportedly requires recording sales and cancellation calls and providing the recording on request. [S, unverified; amendment number uncertain] — [martindale.co.il](https://www.martindale.co.il/%D7%97%D7%95%D7%A7-%D7%94%D7%92%D7%A0%D7%AA-%D7%94%D7%A6%D7%A8%D7%9B%D7%9F/)
- Anti-spam (Communications Law s.30א): no advertisement may be sent by fax, auto-dialer, electronic message or SMS without the recipient's prior express consent, in writing. Damages up to NIS 1,000 per message without proof of harm, cumulative. Courts often award less, for example NIS 800–1,000 per message in the HOT cases. [S+] — [Kol Zchut](https://www.kolzchut.org.il/he/פיצוי_בגין_משלוח_דברי_פרסומת_ללא_הסכמה_של_הנמען_(חוק_הספאם)); [ynet: HOT](https://www.ynet.co.il/articles/mobile/0,7340,L-4915701,00.html); [Chamber of Commerce](https://www.chamber.org.il/serviceslobby/legal/74023/115485/)

### Inferences
- [E — recollection, verify] Other rules likely to matter:
  - **s.13ד:** consumers may cancel an ongoing transaction (עסקה מתמשכת) by notice, through the same channels used to sign up (including online). The trader must stop charging within 3 business days.
  - **Fixed-term deals:** for fixed-term deals with auto-renewal, the trader must notify before the term ends. Recent amendments restrict automatic renewal without fresh consent.
  - **Before payment:** under s.14ג and the distance-selling disclosures, show the trader's identity and address, the total price, what is included and the cancellation terms. Send a transaction-details document.
- [E] A per-plate report delivered instantly may be argued to be an "information product" (exempt) or a "service already provided". Whether the 14-day right applies is uncertain. Design a clear refund policy. [LAWYER]
- [E] Marketing: separate, unticked opt-in for newsletters and SMS; include an unsubscribe in every message. The "existing customer" exception exists but has conditions that I could not verify.

### Gaps
- Not verified: the exact text of s.13ד, the auto-renewal amendment numbers and dates, the s.30א(ג) existing-customer exception, and the "Amendment 70" call-recording rule.

---

## Q7. Website accessibility (Equal Rights for Persons with Disabilities, service accessibility regulations; IS 5568 / WCAG 2.0 AA)

### Takeaway
Regulation 35 of the Service Accessibility Regulations 2013 requires internet services to meet IS 5568 at level AA, based on WCAG 2.0. Regulation 35ה requires an accessibility statement. Website accessibility is a very common ground for class actions. Recent rulings reportedly require a prior demand to fix before suing.

### Cited Findings
- Regulation 35(א): internet services must meet IS 5568. [S+] — [Knesset committee document (PDF)](https://fs.knesset.gov.il/20/Committees/20_cs_bg_390611.pdf); [ISOC-IL](https://www.isoc.org.il/freedom-of-internet/accessibility/legal-aspects-accessibility)
- IS 5568 part 1 adopts WCAG 2.0 AA with Israeli adjustments. An accessibility statement is required (reg. 35ה). [S] — [ronen-web](https://ronen-web.com/website-accessibility-law-israel/); [OCW](https://ocw.co.il/blog/%D7%94%D7%A0%D7%92%D7%A9%D7%AA-%D7%90%D7%AA%D7%A8-%D7%AA%D7%A7%D7%9F-5568/)
- Regulation 35 is one of the most frequent grounds for class-action motions. A court ruling requires plaintiffs to give the site owner prior notice to fix defects first. [S] — [Israel Hayom](https://www.israelhayom.co.il/mumlazim/article/15176590); [Goldfarb Gross Seligman update](https://www.goldfarb.com/he/update/%D7%A0%D7%92%D7%99%D7%A9%D7%95%D7%AA-%D7%A8%D7%99%D7%91%D7%95%D7%99-%D7%AA%D7%95%D7%91%D7%A2%D7%A0%D7%95%D7%AA-%D7%99%D7%99%D7%A6%D7%95%D7%92%D7%99%D7%95%D7%AA-%D7%95%D7%93%D7%A8%D7%9B%D7%99/)
- The duty rests on the site owner and cannot be passed to the developer. [S, vendor view] — [vee.co.il](https://vee.co.il/web-accessibility-5568/)

### Inferences
- [E] Build to WCAG 2.0 AA from day one (consider 2.1 as a buffer), publish an accessibility statement with a contact person, and avoid relying only on "overlay" widgets. [E, recollection, not verified this session] Section 19נח(?) of the Equal Rights Law gives statutory damages without proof of harm of up to about NIS 50,000 (index-linked). Not verified.

### Gaps
- Not verified: the statutory-damages amount for accessibility breaches and the exact case requiring a prior demand.

---

## Cross-cutting risk summary (my estimate, for the report writer)

| Risk | Could it block the business? | Level [E] |
|---|---|---|
| Plate and ownership data treated as personal information; "data trader" classification leads to registration, DPO, high security level and fines | Constrains; it does not block if limited to MoT open fields with compliance | High [LAWYER] |
| Showing or enriching owner identity, or using leaked data | Would block (criminal and regulatory) | Critical: avoid |
| Accident or insurance-claim data from non-government sources | Depends on the source's legal basis and contract | Medium–High [LAWYER] |
| data.gov.il licence (attribution, terms) | Low if attribution is followed | Low |
| Scraping Carzone or Yad2 | Constrains (terms-of-use, copyright on original content, privacy of listings) | Medium: avoid |
| Wrong-information liability | Constrains (disclaimers, insurance) | Medium |
| Consumer law (cancellation, subscriptions, disclosures), anti-spam | Compliance burden; class-action exposure | Medium |
| Accessibility (IS 5568) | Class-action exposure | Medium |

Network note for re-verification: allow www.gov.il, nevo.co.il, fs.knesset.gov.il, data.gov.il, carzone.co.il and yad2.co.il. That would let these [S] items be upgraded to [V].
