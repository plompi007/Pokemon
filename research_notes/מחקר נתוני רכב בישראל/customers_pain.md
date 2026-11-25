# Customer segments, jobs-to-be-done and pain points for vehicle information in Israel

Date checked for all items: 2026-11-25.

**Method note (read first):** In this session WebFetch was blocked for every Israeli host I tried (auto.co.il, carzone.co.il, gov.il, cars.walla.co.il all failed DNS resolution through the sandbox network). Every finding below therefore comes from **WebSearch result summaries/snippets, not from opening the page**. Confidence labels:
- "secondary (snippet)": a claim quoted in a search result summary of the cited URL. The page itself was not opened, so treat wording and numbers as needing verification.
- "verified in primary source": none in this file. I could not open any page.
- "my estimate": my own reasoning, flagged as such.
Facebook groups, Tapuz, Google reviews of report sites and Reddit r/Israel could not be reached (no results or no fetch). There are almost no first-person quotes. See the Gaps sections.

---

## 1. Private used-car buyers: the buying process, when they look up a plate, with which tools, and what they fear

### Takeaway
The Israeli process is: listing (mostly Yad2) → plate lookup (free Ministry of Transport (MoT) data or apps) → price list (Levi Itzhak / Yad2) → lien check (11 ILS) → insurance-claims history (about 10 ILS, from the insurers' clearing house) → inspection at a licensed institute (about 350–700 ILS) → ownership transfer online or at the post office. The main fears are rolled-back mileage, hidden accidents and total-loss ("אובדן להלכה"), and former lease, rental or taxi use. Information is spread across several sources, each partial. There is no single public accident register.

### Cited Findings
**Process steps and costs**
- Pre-purchase inspections follow MoT procedure 127. A dedicated professional licence is required, and the inspection form is identical in all licensed institutes — [auto.co.il](https://www.auto.co.il/article/134065-industry); [auto.co.il](https://www.auto.co.il/articles/car-news/local-news/used-car-inspection/) — secondary (snippet).
- Inspection prices conflict: one source says 350–700 ILS, another 350–600 ILS — [d.co.il price list](https://www.d.co.il/priceList-28290/); [icar.co.il](https://www.icar.co.il/מדריכים/קנייה_מיד_שניה:_בדיקה_במכון/) — secondary (snippet); **contradiction** (small).
- Even a good inspection "gives only a partial picture" ("אל תסמכו רק על מכון הבדיקה"). An ordinary garage is not a full substitute — [auto.co.il](https://www.auto.co.il/articles/car-news/local-news/used-car-inspection/) — secondary (snippet).
- The inspection institute will **not** reveal whether the car was declared אובדן להלכה, so history reports are a complement to the inspection, not a replacement — [check-car.co.il guide](https://www.check-car.co.il/madrich/bdikat-rechev-lifnei-knia/); [ktb.co.il](https://ktb.co.il/article-car-insurance-used-car-check.html) — secondary (snippet).
- A lien check (שעבודים/משכונות) costs 11 ILS at the Ministry of Justice pledges registrar — [bizportal](https://www.bizportal.co.il/car/news/article/20035337) — secondary (snippet).
- Ownership transfer can be done in the MoT personal area online or at a post office — same search result set ([bizportal](https://www.bizportal.co.il/car/news/article/20035337)) — secondary (snippet).
- Insurance-claims history comes from מרכז הסליקה של חברות הביטוח (a subsidiary of the Israel Insurance Association). It costs about 10 ILS per plate, covers up to 7 years back, and shows coverage type, insurer and paid claims — [Israel Hayom](https://www.israelhayom.co.il/article/738715); [ynet](https://www.ynet.co.il/articles/0,7340,L-5048207,00.html) — secondary (snippet).
- **Contradiction:** ynet describes the claims data as available only to the registered owner, while Israel Hayom describes it as open to the public. Commercial resellers say their report "requires the owner's consent and cooperation" — [ynet](https://www.ynet.co.il/articles/0,7340,L-5048207,00.html); [Israel Hayom](https://www.israelhayom.co.il/article/738715); [konesonline](https://www.konesonline.co.il/statuscar/%D7%A2%D7%91%D7%A8-%D7%91%D7%99%D7%98%D7%95%D7%97%D7%99-%D7%9C%D7%A4%D7%99-%D7%9E%D7%A1%D7%A4%D7%A8-%D7%A8%D7%9B%D7%91) — secondary (snippet).
- The claims database omits accidents settled without insurers, repairs paid privately, and periods with no insurance. One provider's terms say the data "may be inaccurate or incomplete" — [ynet](https://www.ynet.co.il/articles/0,7340,L-5048429,00.html); [datahelp](https://datahelp.co.il/check-car-insurance.asp) — secondary (snippet).
- "In Israel there is no public database documenting accidents by plate for private cars", so the clearing-house report is the main accident tool — [check-car.co.il](https://www.check-car.co.il/madrich/bdikat-rechev-lifnei-knia/) (via search summary) — secondary (snippet).

**Market size (how often the job happens)**
- There were 1,316,302 used-car ownership transfers in 2025, against 1,293,862 in 2024 (+1.7%). The source is MoT data as reported by Calcalist. Some of these are 0-km cars passing through importers or lessors — [Calcalist](https://www.calcalist.co.il/local_news/car/article/sjwlh3hhzg) — secondary (snippet). Note: a transfer is not the same as a consumer purchase. It includes dealer, lessor and importer transfers.

**Plate lookup moment and tools**
- MoT "private vehicle history" database (מאגר היסטוריית כלי רכב פרטיים): plate search shows accumulated mileage, colour or tyre changes, and similar fields. It covers active private cars from 2017 onward — [gov.il](https://www.gov.il/he/departments/dynamiccollectors/private_vehicle_history_1) — secondary (snippet).
- Since 1 Jan 2010, licensing institutes write the odometer reading at the annual test on the licence, and it is sent to the MoT database — [cars.walla](https://cars.walla.co.il/item/1623859) (via search summary) — secondary (snippet).
- Many free apps exist that wrap MoT open data (data.gov.il): "רכב ישראל" (mileage from last test, disabled-badge status, MoT garages), CheckCar (camera plate scan, daily MoT updates), "לוחית" (number of hands, recalls, test status), Autoil, and "רכבי ישראל" (ads, with a paid subscription to remove them). Only one rating was surfaced: "חיפוש פרטי רכב לפי מספר רישוי" at 4.2 stars from 338 reviews — [Google Play ilcars](https://play.google.com/store/apps/details?id=com.user.ilcars&hl=en_US); [Google Play Nakash](https://play.google.com/store/apps/details?id=com.nakash.Lightup&hl=en_US); [CheckCar](https://play.google.com/store/apps/details?id=il.co.pat.checkcar&hl=en_US); [לוחית](https://play.google.com/store/apps/details?id=com.ddsabag.pratirechev); [Autoil](https://apps.apple.com/il/app/autoil-%D7%97%D7%99%D7%A4%D7%95%D7%A9-%D7%A8%D7%9B%D7%91-%D7%9C%D7%A4%D7%99-%D7%9E%D7%A1%D7%A4%D7%A8/id6450055352?l=he); [רכבי ישראל](https://play.google.com/store/apps/details?id=com.bumapps.rehevisrael&hl=en_US) — secondary (snippet).
- Paid or freemium report sites competing with Carzone include CarDNA (accidents, value drops, ownership, liens, mileage; it has a "dealers" tag), check-car.co.il (free report), autoboom.co.il (mileage history, insurance history, police stolen-vehicle check; it says data may be missing for some vehicles and advises asking the owner), mtsg.co.il, find-car, data-auto, info-car, asmachta — [cardna.co.il](https://cardna.co.il/); [check-car.co.il](https://www.check-car.co.il/); [autoboom](https://autoboom.co.il/en/check-car/1716566); [mtsg](https://mtsg.co.il/car-check.html); [asmachta](https://asmachta.co.il/insurance-history/) — secondary (snippet).
- Carzone's own description: ownership history, suspected mileage tampering ("over 70 thousand vehicles" flagged), originality, past ads with photos, price list, theft records. Registration gives 2 free reports. Data for cars older than about 8 years is incomplete because the MoT does not publish extended data for them. The site says its data "may contain errors, defects and gaps" — [carzone.co.il](https://carzone.co.il/); [carzone car-report](https://www.carzone.co.il/car-report); [carzone terms](https://www.carzone.co.il/terms) — secondary (snippet).

**Scams and concerns**
- Mileage rollback ("גלגול קילומטראז'"): Carzone estimates over 15,000 vehicles are tampered with each year (an industry estimate, not an official figure) — [carzone kmTampering](https://www.carzone.co.il/news/kmTampering/) — secondary (snippet; it is the competitor's own marketing).
- auto.co.il, citing Carfax data, reports a 14% rise in odometer fraud in 2025 compared with 2024. The underlying Carfax report was not found — [auto.co.il](https://www.auto.co.il/articles/car-news/industry/used-car-mileage-fraud/) — secondary (snippet).
- Personal and parallel imports carry more risk because of information gaps between foreign databases and Israeli licensing records. The average buyer loss is about €2,000. The MoT personal-import database has no detailed mileage — [auto.co.il imported](https://www.auto.co.il/articles/car-news/industry/imported-cars-mileage-fraud/); [gov.il personal import DB](https://www.gov.il/he/service/personalimport-vehicle-database) — secondary (snippet).
- carVertical estimates that a rollback can raise sale price by up to 25%, and that cross-border cars are more likely to have fake histories (a vendor claim, not Israel-specific) — [carVertical](https://www.carvertical.com/transparency-index/metrics) — secondary (snippet; vendor).
- Anecdote (mako): a buyer bought a car showing 45,000 km that had really driven 114,000 km. The headline speaks of "hundreds of drivers" who bought cars with forged odometers — [mako](https://www.mako.co.il/finances-consumer/Article-04c6d922bf9a771027.htm) — secondary (snippet); anecdote plus an unquantified claim.
- Law-firm article: mileage fraud "often comes in one package with hiding an accident" — [pelleg-law](https://pelleg-law.co.il/%D7%96%D7%99%D7%95%D7%A3-%D7%A7%D7%99%D7%9C%D7%95%D7%9E%D7%98%D7%A8%D7%90%D7%96-%D7%91%D7%99%D7%98%D7%95%D7%9C-%D7%A2%D7%A1%D7%A7%D7%94/) — secondary (snippet).
- Former lease, rental or taxi cars: the original ownership type (בעלות מקורית) in MoT data shows lease, taxi or rental use. These cars usually had more intensive use. Buyers should check clutch, brakes, A/C and any LPG conversion. Lease and company cars may carry a lien to a bank or financier — [check-car.co.il](https://www.check-car.co.il/madrich/bdikat-rechev-lifnei-knia/); [mcars.co.il](https://mcars.co.il/blog/rechev-shehaya-monit-o-rechev-chevra) — secondary (snippet).
- A lease car counts as "a second hand" (יד שנייה) even if it arrived at 0 km, and it is priced accordingly — [midrag](https://www.midrag.co.il/Midragonim/Answer/25053) — secondary (snippet).
- Total loss / אובדן להלכה (טוטאלוס): the seller must disclose it. Failing to do so allows cancelling the deal. The Consumer Protection Authority's legal adviser issued an opinion that safety damage or אובדן להלכה must be stated already in the advertisement, otherwise it is misleading under the Consumer Protection Law (the article is old, so current status is unverified) — [nws.report](https://nws.report/shoping/68932/); [blitshtein-law](https://www.blitshtein-law.com/%D7%A2%D7%95%D7%A8%D7%9A-%D7%93%D7%99%D7%9F-%D7%9C%D7%A2%D7%A0%D7%99%D7%99%D7%A0%D7%99-%D7%A8%D7%9B%D7%91/%D7%90%D7%95%D7%91%D7%93%D7%9F-%D7%92%D7%9E%D7%95%D7%A8-%D7%9C%D7%94%D7%9C%D7%9B%D7%94/); [balcar](https://balcar.co.il/guides/car-total-loss) — secondary (snippet).
- The Used Car Sale (Right to Information and Disclosure) Law 2008 applies only to dealers (עוסקים). Private-to-private sales are outside it. The disclosure form must include damage, mileage and price — [Wikipedia](https://he.wikipedia.org/wiki/%D7%97%D7%95%D7%A7_%D7%9E%D7%9B%D7%99%D7%A8%D7%AA_%D7%A8%D7%9B%D7%91_%D7%9E%D7%A9%D7%95%D7%9E%D7%A9_(%D7%96%D7%9B%D7%90%D7%95%D7%AA_%D7%9C%D7%9E%D7%99%D7%93%D7%A2_%D7%95%D7%92%D7%99%D7%9C%D7%95%D7%99_%D7%A0%D7%90%D7%95%D7%AA)); [motus.co.il](https://motus.co.il/%D7%92%D7%99%D7%9C%D7%95%D7%99-%D7%A0%D7%90%D7%95%D7%AA-%D7%91%D7%9E%D7%9B%D7%99%D7%A8%D7%AA-%D7%A8%D7%9B%D7%91-%D7%9E%D7%A9%D7%95%D7%9E%D7%A9) — secondary (snippet).
- Walla, reporting a Supreme Court ruling: the buyer taking the car to inspection does not exempt the seller from actively disclosing known defects — [cars.walla](https://cars.walla.co.il/item/3322094) — secondary (snippet).
- Disguised dealers on listing boards: a profile posting more than one car may be a dealer posing as a private seller — [auto.co.il](https://www.auto.co.il/articles/guides/buying-used-car/138108/) — secondary (snippet).
- Payment and identity scams on Yad2: scammers use Yad2 branding, foreign WhatsApp numbers, avoid meeting in person and show fake transfer screenshots. One seller listed a car at 100,000 ILS and received a transfer that "disappeared" the next day — [bhol July 2026](https://www.bhol.co.il//news/1511747); [ice.co.il](https://www.ice.co.il/auto/news/article/1076215) — secondary (snippet).
- War-damaged cars: missile damage is not covered by comprehensive insurance. It is compensated by the state through מס רכוש, valued by Levi Itzhak including salvage. No source was found on how such cars show up in the used market, or on flood-damaged cars — [ynet](https://www.ynet.co.il/economy/article/skz1iyt7eg) — secondary (snippet).

### Inferences
- (my estimate) The lookup moment is twice: (a) right after seeing a listing and before calling or visiting, a free and fast screening to filter out bad cars, and (b) after a test drive and before paying for an inspection or putting down a deposit, where a paid, deeper report is justified. Users need to complete a "plate → verdict" check in under a minute.
- (my estimate) The core pain is fragmentation, not missing data. A careful buyer pays for and joins 4–5 sources (MoT free data, lien 11 ILS, claims about 10 ILS with owner consent, price list, inspection 350–700 ILS). A product that bundles these and interprets them ("red flags") addresses the actual job.
- (my estimate) The owner-consent requirement for claims history creates friction during private deals. A "seller-shared verified report" flow could solve it.
- With about 1.3M transfers a year, even a few percent paying for reports means tens of thousands of paid reports (my estimate; the transfer count is not the same as the number of buyers).

### Gaps
- No first-person quotes from Facebook groups ("קונים מכוניות יד 2" etc.), Tapuz or Reddit. These could not be accessed. There are only two forum snippets (carsforum.co.il, below in section 5).
- No survey data on what share of buyers check a plate, pay for a report, or skip the inspection.
- No data on flood-damaged cars, or on how war-damaged cars are flagged in MoT data.
- MoT's official "buying a used car" guidance and the Consumer Protection Authority's current guidance pages could not be opened (gov.il blocked).

---

## 2. Sellers: do they use reports to price or to prove quality?

### Takeaway
Not found as evidence. The sources cover sellers mainly as targets of payment scams and as subjects of disclosure duties. No source shows private sellers buying reports to prove quality.

### Cited Findings
- Price lists are the default pricing tool. Levi Itzhak is "considered authoritative in the insurance and appraisal sector" and some call it a monopoly. Yad2 has a free price list (adopted by an appraisers' association in 2010). MoT launched "מחירון העם" (based on reported sales) in 2021 — [Wikipedia מחירון לוי יצחק](https://he.wikipedia.org/wiki/%D7%9E%D7%97%D7%99%D7%A8%D7%95%D7%9F_%D7%9C%D7%95%D7%99_%D7%99%D7%A6%D7%97%D7%A7); [Haaretz 2010](https://www.haaretz.co.il/misc/2010-03-22/ty-article/0000017f-f47f-d887-a7ff-fcff21e30000); [Globes](https://www.globes.co.il/news/article.aspx?did=1000613392) — secondary (snippet).
- The Levi Itzhak app supports plate lookup and adjusts price for number of owners (יד), mileage and equipment — [levi-itzhak.co.il](https://levi-itzhak.co.il/%D7%A8%D7%9B%D7%91); [Google Play](https://play.google.com/store/apps/details?id=com.levinew.app&hl=en_US) — secondary (snippet).
- Templates for a seller disclosure form exist (motus.co.il), which suggests some sellers want to document the car's condition — [motus.co.il](https://motus.co.il/%D7%92%D7%99%D7%9C%D7%95%D7%99-%D7%A0%D7%90%D7%95%D7%AA-%D7%91%D7%9E%D7%9B%D7%99%D7%A8%D7%AA-%D7%A8%D7%9B%D7%91-%D7%9E%D7%A9%D7%95%D7%9E%D7%A9) — secondary (snippet).

### Inferences
- (my estimate) Sellers of clean, low-mileage cars have a reason to share a verified report in their listing to justify a premium. This is untested in Israel. Treat it as a hypothesis for interviews.

### Gaps
- No data on sellers paying for reports, and no Yad2 feature data on attaching reports to listings.

---

## 3. B2B: dealers, garages, leasing companies, insurers, appraisers, fleets. Existing tools and willingness to pay

### Takeaway
B2B tools exist in pieces: Levi Itzhak subscriptions, commercial plate APIs (rechevapi), free MoT CKAN open data that needs no API key, and the insurers' clearing house. I found no public evidence of a "Carzone Pro" dealer product, of Levi Itzhak B2B or API terms, or of what leasing companies and insurers use internally. B2B willingness to pay is unproven by sources.

### Cited Findings
- rechevapi.co.il sells an API (.NET ASMX/SOAP) that returns make, model, fuel, VIN and about 20 fields from an Israeli plate, "in real time from official government databases". No pricing was found — [rechevapi.co.il](http://www.rechevapi.co.il/) — secondary (snippet).
- A 2026 developer guide says MoT vehicle records can be fetched by plate through a plain GET to the data.gov.il CKAN datastore, with no authentication and no key, and that there is no "classic REST API" — [car.lior-ai.com](https://car.lior-ai.com/vehicle-data-api-israel.html) — secondary (snippet). Implication: basic data is a commodity, so B2B value must come from aggregation and analytics.
- CarDNA tags "סוחרי רכב" (dealers) as a service. Details are unknown — [cardna.co.il](https://cardna.co.il/) — secondary (snippet).
- Levi Itzhak sells annual price-list subscriptions and an app. Its prices come from monthly surveys of dealers and private sellers. It is the reference in insurance and appraisal (מס רכוש also uses it for war-damage compensation) — [levi-itzhak.co.il](https://levi-itzhak.co.il/%D7%9E%D7%97%D7%99%D7%A8%D7%95%D7%9F-%D7%A8%D7%9B%D7%91); [ynet](https://www.ynet.co.il/economy/article/skz1iyt7eg) — secondary (snippet).
- Insurers share claims through מרכז הסליקה (Insurance Association subsidiary). That database is an insurer-owned asset — [Israel Hayom](https://www.israelhayom.co.il/article/738715) — secondary (snippet).
- CarPay offers escrow-style payment plus accident and insurance history verification for private deals — [JPost](https://stgmobile.jpost.com/business-and-innovation/article-747087) — secondary (snippet).
- Carzone dealer subscription pricing: **not found** — [carzone.co.il](https://carzone.co.il/) — search result.

### Inferences
- (my estimate) Dealers have the highest lookup frequency (many cars per week for trade-in and stock pricing). They are the most plausible paying B2B segment for bulk lookups plus price-trend dashboards. Garages need service-history logging, which could also become a data source. Lessors and insurers likely already hold their own data and are more plausible as data partners than as customers.

### Gaps
- No evidence of Levi Itzhak B2B or API products, MoT dealer systems, leasing-company remarketing tools, fleet-manager tools, or insurer underwriting data vendors. There are no interviews or pricing.
- No dealer forum or association material (e.g., איגוד סוחרי הרכב) was found.

---

## 4. Information buyers want but can't get

### Takeaway
Gaps that sources repeatedly mention: full accident history (no public register; insurer data needs consent and misses unreported repairs), reliable mileage before 2010/2017 and for imported cars, service history (held by garages and not public), and extended data for cars older than about 8 years.

### Cited Findings
- No public accident register for private cars — [check-car.co.il](https://www.check-car.co.il/madrich/bdikat-rechev-lifnei-knia/) — secondary (snippet).
- Claims data needs owner consent and misses unreported accidents — [ynet](https://www.ynet.co.il/articles/0,7340,L-5048429,00.html); [konesonline](https://www.konesonline.co.il/statuscar/%D7%A2%D7%91%D7%A8-%D7%91%D7%99%D7%98%D7%95%D7%97%D7%99-%D7%9C%D7%A4%D7%99-%D7%9E%D7%A1%D7%A4%D7%A8-%D7%A8%D7%9B%D7%91) — secondary (snippet).
- MoT history database covers active private cars only from 2017 — [gov.il](https://www.gov.il/he/departments/dynamiccollectors/private_vehicle_history_1) — secondary (snippet).
- MoT does not publish extended data for older cars (more than about 8 years), according to Carzone — [carzone car-report](https://www.carzone.co.il/car-report) — secondary (snippet).
- Forum advice is to call the authorised garage and ask for the last-service mileage, which shows that service history is reached manually — [carsforum.co.il](https://carsforum.co.il/topic/674680-%D7%97%D7%A9%D7%93-%D7%9C%D7%A7%D7%99%D7%9C%D7%95%D7%9E%D7%98%D7%A8%D7%90%D7%96-%D7%9E%D7%96%D7%95%D7%99%D7%A3-%D7%90%D7%99%D7%9A-%D7%90%D7%A4%D7%A9%D7%A8-%D7%9C%D7%91%D7%93%D7%95%D7%A7-%D7%9E%D7%94-%D7%94%D7%99%D7%94-%D7%94%D7%A7%D7%99%D7%9C%D7%95%D7%9E%D7%98%D7%A8%D7%90%D7%96-%D7%91%D7%98%D7%A1%D7%98%D7%99%D7%9D-%D7%A7%D7%95%D7%93%D7%9E%D7%99%D7%9D/) — secondary (snippet).
- For imports, there is "no central mileage database". Buyers rely on foreign documents and seller declarations — [auto.co.il](https://www.auto.co.il/articles/car-news/industry/imported-cars-mileage-fraud/) — secondary (snippet).
- A Knesset bill on mandatory odometer registration in the vehicle register (25th Knesset) exists. Its status was not checked — [Knesset PDF](https://fs.knesset.gov.il/25/law/25_lst_2361038.pdf) — secondary (snippet).

### Inferences
- (my estimate) Ranked by buyer value against how feasible the data is: (1) mileage consistency across tests and past ads (feasible and already Carzone's hook), (2) original ownership type and number of hands (feasible from MoT), (3) accident and total-loss history (high value, gated by consent or partnership), (4) service history (high value, needs garage partnerships), (5) foreign history for imports (needs a Carfax/carVertical partnership).

### Gaps
- No quantitative survey ranking which data points buyers want most.

---

## 5. Real voices (quotes and complaints) and the value proposition and metrics

### Takeaway
Very few real voices could be gathered. There are two carsforum.co.il snippets and one mako anecdote. The value proposition and metrics below are my own proposals.

### Cited Findings
- carsforum user (suspected mileage fraud thread): "באתר CARZONE אפשר לראות את הק"מ בטסטים / מודעות למכירה ישנות כמה שנים אחורה". Another reply: "הדרך הפשוטה ביותר (וגם החוקית) לבדוק את אמינות מד המרחק - היא להתקשר למוסך מורשה" — [carsforum 674680](https://carsforum.co.il/topic/674680-%D7%97%D7%A9%D7%93-%D7%9C%D7%A7%D7%99%D7%9C%D7%95%D7%9E%D7%98%D7%A8%D7%90%D7%96-%D7%9E%D7%96%D7%95%D7%99%D7%A3-%D7%90%D7%99%D7%9A-%D7%90%D7%A4%D7%A9%D7%A8-%D7%9C%D7%91%D7%93%D7%95%D7%A7-%D7%9E%D7%94-%D7%94%D7%99%D7%94-%D7%94%D7%A7%D7%99%D7%9C%D7%95%D7%9E%D7%98%D7%A8%D7%90%D7%96-%D7%91%D7%98%D7%A1%D7%98%D7%99%D7%9D-%D7%A7%D7%95%D7%93%D7%9E%D7%99%D7%9D/) — secondary (snippet); anecdote.
- carsforum user: "...בדיקת עבר ביטוחי וגיליתי שהייתה תאונה שהורידה 2% מערך הרכב שלא ידעתי עליה" — [carsforum 676916](https://carsforum.co.il/topic/676916-%D7%A0%D7%A4%D7%9C%D7%AA%D7%99-%D7%A2%D7%9C-%D7%A1%D7%95%D7%97%D7%A8-%D7%A9%D7%96%D7%99%D7%99%D7%A3-%D7%A7%D7%99%D7%9C%D7%95%D7%9E%D7%98%D7%A8%D7%96-%D7%95%D7%9E%D7%A6%D7%91-%D7%94%D7%A8%D7%9B%D7%91-%D7%A9%D7%A7%D7%A0%D7%99%D7%AA%D7%99/) (thread titled "נפלתי על סוחר שזייף קילומטרז") — secondary (snippet); anecdote.
- mako: 45k km shown against 114k km actual. In one case the seller claimed he did not know about the forgery — [mako](https://www.mako.co.il/finances-consumer/Article-04c6d922bf9a771027.htm) — secondary (snippet); anecdote.
- Commenter on an ICE article: could not reach a Yad2 seller by WhatsApp or SMS — [ice.co.il](https://www.ice.co.il/auto/news/article/1076215) (via search summary) — anecdote.
- No independent user reviews of Carzone were found (no Trustpilot or Google review results surfaced) — search result for "carzone ביקורות" — **not found**.

### Inferences (all my estimate)
- One-sentence value proposition (draft): "Enter a plate and in 30 seconds get one clear verdict on whether this car is honest: real mileage, previous owners and ownership type, accidents and total-loss, liens and a fair price, all in one report for less than a tank of fuel."
- B2B variant: "Price and vet every trade-in in seconds: bulk plate lookups, mileage-anomaly flags and market-price trends via dashboard or API."
- How to measure time and money saved:
  - Money: avoided overpayment. Rollback can inflate price up to 25% (vendor claim, [carVertical](https://www.carvertical.com/transparency-index/metrics)). The average import-fraud loss is about €2,000 ([auto.co.il](https://www.auto.co.il/articles/car-news/industry/imported-cars-mileage-fraud/)). Also avoided wasted inspections at 350–700 ILS each on cars a report would have screened out. KPI: share of reports with a red flag, multiplied by the average inspection fee and the average price gap.
  - Time: count of separate sources and steps replaced (MoT lookup, lien check, claims report with owner consent, price list, calls to the garage), and minutes from plate to decision. KPI: median time-to-verdict, and number of cars screened per purchase.
  - B2B: lookups per dealer per month, time per trade-in appraisal, and margin protected per car.

### Gaps
- Facebook group posts, Tapuz threads, r/Israel, Google Play review text and Google reviews of report sites could not be retrieved. The report writer should treat the "voices" evidence as thin.
- No benchmarks for willingness-to-pay (ILS per report) beyond the low price points of the components (10–11 ILS for official reports) and Carzone's 2 free reports.
