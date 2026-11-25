# Go-to-market, unit economics, payments and paid data for an Israeli vehicle-report site/app (vs. carzone.co.il)

Date checked for all items: 2026-11-25. Confidence labels: **[V]** = verified in primary source; **[S]** = secondary source (search-engine summary of the page, aggregator, press, or vendor-adjacent page; full page not fetched); **[E]** = my estimate.

Method note, which affects confidence: this session's network blocked direct fetches of carvertical.com, carzone.co.il and auto.co.il. For those sites I only had search-engine summaries, so their claims are labeled [S]. Of the pages I tried to fetch, only developer.apple.com loaded. I ran about 19 searches and fetches.

---

## 1. Paid and proprietary data sources in Israel

### Takeaway
The one important paid source with a known price is the insurers' property-claims database, run by the insurers' clearing center (מרכז הסליקה של חברות הביטוח). It costs about 10–12 ₪ per plate and needs the owner's consent. Carzone does not include it and sends users to it separately. I found no public API or licensing terms for Levi Itzhak (לוי יצחק) or for Yad2's price list. Importer service history, leasing-company records, odometer data beyond the gov.il data, and auction data are all "not found" as products that third parties can buy.

### Cited Findings
- **Insurance claims database.** The clearing center is a subsidiary of the Israel Insurance Association (איגוד חברות הביטוח). It pools insurers' reports of property-damage claims they paid on insured vehicles. It shows the damage type (total loss, consequential damage, theft), the amounts paid, and whether a claim is still open. It does not include accidents the parties kept away from insurers. Price is reported as 10 ₪ per check by plate. [S] — [icar.co.il](https://www.icar.co.il/חדשות_רכב/שירות_חדש_יעניק_מידע_על_עבר_ביטוחי_לרכב_משומש/); [auto.co.il](https://www.auto.co.il/article/129901-local-news)
- **Contradiction on coverage period.** One article says the data covers the last 7 years, another says the last 10. Unresolved. [S] — same sources as above.
- **Carzone's handling.** Carzone's report does not query the clearing center. It says a separate clearing-center report costs about 12 ₪ and requires the owner's consent. [S] — [carzone.co.il/car-report](https://www.carzone.co.il/car-report); [carzone.co.il/slika](https://www.carzone.co.il/slika)
- **Har HaBituach (הר הביטוח) is a different thing.** It is the Capital Market Authority's portal, where an insured person, after simple identification, gets a free consolidated insurance-history report from all insurers. It is keyed to the person, not to a vehicle sold to third parties. Since 2022, claims for not-at-fault accidents where at least 75% of the damage was recovered from a third party are excluded from that report. [S] — [fnx.co.il](https://www.fnx.co.il/car-insurance/car_information/new-law-on-history/); [calcalist](https://www.calcalist.co.il/articles/0,7340,L-3794410,00.html)
- **Gaps on third-party access.** I found no official source on whether a third party (a reporting site, garage or appraiser) can get bulk or API access to the clearing-center database or Har HaBituach. "Not found."
- **Levi Itzhak.** It publishes a monthly price list and has operated since 1971 [S] — [colmobil.co.il](https://www.colmobil.co.il/car_guide/levi_yitzchak/). Its site sells a yearly price-list subscription [S] — [levi-itzhak.co.il/רכב](https://levi-itzhak.co.il/%D7%A8%D7%9B%D7%91); [printed yearly subscription page](https://levi-itzhak.co.il/%D7%9E%D7%97%D7%99%D7%A8%D7%95%D7%9F-%D7%A8%D7%9B%D7%91-%D7%9E%D7%A0%D7%95%D7%99-%D7%A9%D7%A0%D7%AA%D7%99). One source gives 840 ₪ for a single price list for 12 months, but that is a print or consumer subscription, not a data license [S], and the price may be old. The consumer app is free and looks up by plate or by make, model and year [S] — [App Store](https://apps.apple.com/app/id1478184705); [Google Play](https://play.google.com/store/apps/details?id=com.levinew.app&hl=en_US). **API or B2B data-licensing terms: not found.**
- **Yad2 price list.** Press compares it with Levi Itzhak [S] — [auto.co.il](https://www.auto.co.il/articles/leasing/120926/). **Licensing or API terms: not found.**
- **Free government data.** gov.il publishes a private-vehicle history dataset with odometer readings and vehicle changes for cars active since 2017. A second dataset gives the number of previous owners and the ownership type. [S] — [gov.il private_vehicle_history_1](https://www.gov.il/he/Departments/DynamicCollectors/private_vehicle_history_1). There is also a gov.il stolen-vehicle lookup by plate [S] — [gov.il](https://www.gov.il/he/service/licence_plate_stolen_vehicle_identification).
- **What carzone already offers.** Ownership history, originality, past listings with photos, price-list ranges by trim, originality and mileage, theft, mileage reports, and past use such as rental or taxi. It admits extended data is often missing for cars older than about 8 years. New users get 2 free reports. [S] — [carzone.co.il](https://carzone.co.il/); [carzone.co.il/car-report](https://www.carzone.co.il/car-report)

### Inferences
- [E] Real paid differentiation is narrow. The only verified per-plate paid source (the clearing center) is consent-gated and per-person. So it is more realistic as a guided "ask the seller to pull it" flow, or a partner integration negotiated with the insurers' association, than as automatic data. Treat any B2B deal as a negotiation with an unknown price.
- [E] Licensing a price list (Levi Itzhak or Yad2) would probably be a negotiated B2B deal. Carzone already shows price-list ranges, so this is parity, not differentiation.
- [E] Importer service records and leasing fleet records would need bilateral data deals. Plausible partners are the big importers (for example Colmobil, Delek Motors, UMI) and leasing companies. There is no public market for this data.

### Gaps
- Levi Itzhak and Yad2 API pricing; clearing-center B2B access; importer, dealer, auction and odometer data products. All not found and would need direct sales contact.
- Contradiction: 7 vs 10 years of claims coverage.

---

## 2. Data that can be built in-house

### Takeaway
A historical archive of listings and government data is the most defensible asset that can be built in-house. Scraping listings in Israel is legally grey. Raw facts were held not protected as a compilation in Maariv v. AllJobs, but unjust enrichment, terms of service and privacy-law exposure remain. It needs a legal opinion.

### Cited Findings
- **Maariv v. AllJobs.** In the Tel Aviv District Court, reusing raw data from job ads (not their wording) was held not to be a protected "compilation" for lack of originality. The court also noted that unjust-enrichment doctrine can protect a developer against copying even without a recognized property right. [S] — [fridmanwork.com summary](https://www.fridmanwork.com/ADVX-lawyers111699.html)
- **Database protection is unsettled.** Israeli case law is unclear on whether "sweat of the brow" or originality governs protection of databases. [S] — [TheMarker 2004](https://www.themarker.com/law/2004-12-02/ty-article/0000017f-ef43-dc28-a17f-ff77858c0000)
- **Privacy exposure.** Unlawful data mining may breach section 8C of the Privacy Protection Law and may be a criminal offense under section 23N (סעיף 23נה). Listings can include sellers' phone numbers and names. [S] — [moticohenadv.com (June 2025 update)](https://moticohenadv.com/%D7%94%D7%90%D7%9D-%D7%9E%D7%95%D7%AA%D7%A8-%D7%9C%D7%91%D7%A6%D7%A2-%D7%A1%D7%A8%D7%99%D7%A7%D7%AA-%D7%90%D7%AA%D7%A8%D7%99%D7%9D-data-scraping/); [fbclawyers.com](https://www.fbclawyers.com/news/%D7%9E%D7%A2%D7%95%D7%93%D7%9B%D7%9F-%D7%A1%D7%99%D7%99%D7%91%D7%A8-%D7%95%D7%98%D7%9B%D7%A0%D7%95%D7%9C%D7%95%D7%92%D7%99%D7%95%D7%AA-%D7%9E%D7%99%D7%93%D7%A2-%D7%90%D7%99%D7%A1%D7%95%D7%A3/); [dubinsky.co.il](https://dubinsky.co.il/he/%D7%9E%D7%94-%D7%97%D7%A9%D7%95%D7%91-%D7%9C%D7%93%D7%A2%D7%AA-%D7%9E%D7%91%D7%97%D7%99%D7%A0%D7%94-%D7%9E%D7%A9%D7%A4%D7%98%D7%99%D7%AA-%D7%9C%D7%92%D7%91%D7%99-%D7%A1%D7%A8%D7%99%D7%A7%D7%AA-%D7%A0/)
- **Carzone already shows past listings with photos for the same car.** So a listings archive is parity, not a moat, unless it is deeper or older. [S] — [carzone.co.il](https://carzone.co.il/)
- **Israel Privacy Protection Law, Amendment 13 (in force August 2025): not checked in this session.** It is relevant to storing listing personal data.

### Inferences
- [E] Lower-risk in-house assets:
  1. Periodic snapshots of the gov.il/CKAN vehicle datasets, to reconstruct odometer and ownership changes over time and to detect plate-level changes.
  2. Price trends by model and year from our own user-submitted or partner-fed listings.
  3. Alerts (test due, recall, price drops on watched models).
  4. User-generated inspection results from partner garages.
- [E] Time to value. Monthly government snapshots give meaningful trend lines after about 6–12 months. Listings-based price indices need roughly 3–6 months of daily collection to be statistically useful for common models, and longer for rare ones.
- [E] Strip personal data (phone numbers, names) from any listings archive at ingestion, to reduce exposure under section 8C.

### Gaps
- No Israeli ruling specific to Yad2 scraping was found. Yad2's terms of service were not checked.

---

## 3. Distribution channels and CAC

### Takeaway
I found no Israel-specific CPC data. Global 2025 Google Ads benchmarks are about $5.26 CPC across all industries and about $3.49–3.90 for automotive. Carfax and carVertical do not publish CAC. carVertical's fast growth (53.9M → 75.8M EUR) shows the category supports heavy paid performance marketing, but its unit numbers are private.

### Cited Findings
- **Google Ads all-industry 2025:** average CPC $5.26 (up from $4.66 in 2024); average conversion rate 7.52%; cost per lead $66.69. [S] — [Search Engine Land](https://searchengineland.com/google-ads-costs-rising-but-conversion-rates-improved-in-2025-477927); [WordStream conversion benchmarks](https://www.wordstream.com/blog/conversion-rate-benchmarks); [WordStream 2025](https://wordstream.com/blog/2025-google-ads-benchmarks)
- **Automotive:** average CPC $3.49 and CTR 6.60% (year unclear) [S] — [LocaliQ automotive](https://localiq.com/blog/automotive-search-advertising-benchmarks/). $3.90 CPC for automotive search, labeled 2025 by a third party [S] — [DemandLocal](https://www.demandlocal.com/blog/google-vehicle-ads-performance-statistics/). Automotive for-sale conversion rate is about 6.01% and repair/service about 14–15.5% (WordStream and SEJ 2026 data) [S] — [SEJ](https://www.searchenginejournal.com/what-are-good-google-ads-benchmarks/546995/). These are mostly US figures.
- **Israel CPC by country:** Statista has dealership CPC by country (Semrush, December 2024), but the Israel value was not visible. Not found. [S] — [Statista](https://www.statista.com/statistics/1402590/automobile-dealerships-googleads-cpc)
- **carVertical:** revenue €53.9M (2024) → €75.8M (2025, +40%). B2B revenue grew 47% (2023), 101% (2024) and 83% (2025). Announced 12 May 2026. [S] — [carVertical blog](https://www.carvertical.com/en/blog/carvertical-revenue-growth); [journalauto.com](https://journalauto.com/services/rapports-dhistorique-carvertical-poursuit-son-ascension/); [autohaus.de](https://www.autohaus.de/nachrichten/gw-trends/expansion-zahlt-sich-aus-carvertical-steigert-umsatz-deutlich-3807960). CAC, marketing spend and reports sold: not found.
- **Carfax:** revenue $928M (2023), $1,039M (2024), $1,142M (FY2025), about 11% CAGR. [V/S: SEC 8-K exhibit, seen via search summary] — [SEC 8-K ex99-1](https://www.sec.gov/Archives/edgar/data/0000064040/000110465926058908/tm2613574d2_ex99-1.htm). S&P Global announced in April 2025 that it will spin off Mobility, which includes Carfax [S] — [Wikipedia](https://wikipedia.com/wiki/Carfax,_Inc.). Carfax promotes free reports attached to listings, a dealer-paid model [S] — [Seeking Alpha PR](https://seekingalpha.com/pr/20292350-carfax-highest-used-car-prices-in-18-months-some-older-models-close-in-price-to-new-models). CAC: not found.
- **Facebook groups, garage, inspection-institute and dealer partnerships, referral loops:** no Israel-specific cost data found.

### Inferences
- [E] Israel Google Ads CPC for plate-lookup terms ("בדיקת רכב לפי מספר", "היסטוריית רכב") is likely in the range of 1.5–6 ₪. Assumptions: a small market, competitors (carzone, cartube and others) bidding, and Hebrew-language auctions usually cheaper than US auctions. Must be validated in Keyword Planner.
- [E] Paid CAC. If CPC is 3 ₪ and landing-to-paid conversion is 2–5%, CAC is 60–150 ₪ per first paid report. That is above a likely report price of about 15–50 ₪ (an assumption; carzone's paid price was not found). So paid search only pays back with bundles, subscriptions for dealers, or high repeat use. SEO and free-lookup virality must carry most acquisition.
- [E] SEO. Plate-lookup head terms are contested by carzone, government pages (gov.il) and others. Long-tail model and year pages ("מחיר יד2 מאזדה 3 2019", "בעיות נפוצות ב...") built from the in-house data are the more realistic SEO wedge.
- [E] B2B partnerships (garages, the pre-purchase inspection institutes מכוני בדיקה, dealers) likely give the lowest CAC per paid report, using rev-share or white-label. This mirrors carVertical's fast B2B growth.

### Gaps
- Israel-specific CPC, CAC, and Facebook CPM for Israeli automotive audiences: not found.

---

## 4. Conversion benchmarks

### Takeaway
There are no public visitor-to-paid figures for vehicle-report sites. General freemium benchmarks are about 2.6–5.8% (average about 3.7%) for SaaS freemium, and likely lower for consumer products.

### Cited Findings
- Freemium self-serve: 3–5% is "good" and 8–12% is "great" [S] — [Ada Chen Rekhi, Medium](https://medium.com/ada-chen-rekhi/freemium-and-free-trial-conversion-benchmarks-9fab38d096da)
- ChartMogul 2026: median free-to-paid is 8% across products; for ungated freemium, a "good" rate is 7–9% [S] — [ChartMogul](https://chartmogul.com/reports/saas-conversion-report/)
- First Page Sage (via CrazyEgg): traditional freemium averages 3.7% (2.6–5.8%), and consumer products may run lower [S] — [CrazyEgg](https://www.crazyegg.com/blog/free-to-paid-conversion-rate/)
- carVertical and Carfax visitor-to-paid conversion: not found.

### Inferences
- [E] For a plate-lookup site where the free tier shows basic gov.il data, model visitor→free lookup at 30–60% and free lookup→paid report at 1–5%. So visitor→paid is roughly 0.5–3%. These are SaaS benchmarks discounted for one-off consumer intent. High-intent paid-search traffic may convert at the top of this range.

### Gaps
- Category-specific conversion data: not found.

---

## 5. Cost per report and payments

### Takeaway
Israeli processors charge about 1.5–1.7% + 1 ₪ per transaction (Grow, via Wix), and that rate covers card, Bit and Apple Pay. Stripe does not serve Israeli-registered merchants. Inside an iOS app, a digital report viewed in the app falls under Apple guideline 3.1.1, so it requires IAP (15–30%). That strongly favors web-first checkout.

### Cited Findings
- **Grow (formerly Meshulam).** Pay-as-you-go: 1.7% + 1 ₪ per transaction for credit card, Apple Pay and Bit, excluding VAT; 1.5% + 1 ₪ at lower monthly volumes. A plan at 59 ₪/month + 1.5% per transaction. These are Wix-listed figures, not Grow's own price list. [S] — [Wix support (EN)](https://support.wix.com/en/article/connecting-grow-by-meshulam-as-a-payment-provider); [Wix (HE)](https://support.wix.com/he/article/חיבור-grow-של-משולם-כחברת-סליקה). Grow's API docs list the accepted methods [S] — [grow-il.readme.io](https://grow-il.readme.io/reference/payments)
- **Tranzila.** Rates are quote-only and a monthly minimum applies; one comparison cites a 97 ₪ minimum [S] — [quasa.io](https://quasa.io/he/media/grow-av-tranzila-mkhyr-glvy-mvl-mynymvm-khvdshy-shl-97-shql). It supports Visa, Mastercard, Amex, Diners, Bit, Apple Pay, Google Pay, PayPal and Masav [S] — [tranzila.com/llms.txt](https://www.tranzila.com/llms.txt)
- **Cardcom.** Holds an acquirer license from the Bank of Israel [S] — [BOI press release](https://boi.org.il/en/communication-and-publications/press-releases/the-bank-of-israel-grants-a-license-to-another-new-acquirer-today/). Pricing: not found.
- **PayPlus pricing:** not found (not searched in depth).
- **Stripe.** Not available to Israeli merchants; it never formally applied for a Bank of Israel acquiring license (Globes; article date unconfirmed). It is reachable only through a foreign entity. [S] — [Globes](https://en.globes.co.il/en/article-1001381078); [Airwallex](https://www.airwallex.com/il/airwallex-vs-stripe)
- **Apple App Store, verified in the primary source.** Guideline 3.1.1: "If you want to unlock features or functionality within your app, (by way of example: subscriptions… access to premium content…), you must use in-app purchase." 3.1.3(e) exempts only "physical goods or services that will be consumed outside of the app." The reader-app exception (3.1.3(a)) covers only magazines, newspapers, books, audio, music and video. Links out to web purchase are allowed only in specific storefronts (the US storefront is called out explicitly). [V] — [Apple App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)
- **Google Play.** All app categories are subject to the Payments policy. Alternative or user-choice billing markets are listed as the EEA, UK, US, Korea, India, Japan, Australia, Brazil, Indonesia and South Africa; Israel is not listed. [S] — [Google Play user choice billing](https://developer.android.com/google/play/billing/user-choice?hl=he); [Google Play Console help](https://support.google.com/googleplay/android-developer/answer/10281818)
- **App store commission rates (30%, or 15% under the small business program and after year one of a subscription):** standard terms from my knowledge, not re-verified this session. [E]
- **Carzone's payment methods and report price:** not found (fetch blocked).
- **Bit vs card vs Apple Pay conversion in Israel:** not found.

### Inferences: per-report cost model [E]
Assumptions: report price 29 ₪ including VAT, sold on the web; Grow at 1.7% + 1 ₪.
- Payment fee: about 1.5 ₪ (about 5% of the price). At 15 ₪ the fee is about 1.26 ₪ (8.4%), so the fixed 1 ₪ hurts low price points. That argues for bundles of 3 or 5 reports.
- VAT (18% in 2025): about 4.4 ₪ of the 29 ₪. VAT rate not re-verified this session.
- Compute, storage and CKAN calls: under 0.05 ₪ per report at low volume, since CKAN is free.
- Support: assume 2–5% of buyers contact support at about 10–20 ₪ fully loaded per ticket, which is about 0.2–1 ₪ per report.
- Optional paid data. Clearing-center pass-through is about 10–12 ₪ retail per check; any wholesale rate is unknown.
- Margin before CAC: about 21–22 ₪ per 29 ₪ report on the web. Via iOS IAP at 15–30%, it is about 14–20 ₪.
- Break-even example. Fixed costs of 15k ₪/month (hosting, tools, part-time support, legal and accessibility upkeep; founders unpaid) at about 21 ₪ contribution need about 710 paid reports a month at zero CAC. With blended CAC of 30 ₪ (mostly SEO), every sale loses money until repeat or bundle revenue arrives. The model only works with blended CAC well under the contribution margin.

### Gaps
- Cardcom, PayPlus and Tranzila actual rates; Bit-specific fees; Israeli payment-method conversion splits.

---

## 6. Website vs app, store policy, RTL and accessibility

### Takeaway
Go web-first, mobile-first and RTL. Apple's 3.1.1 forces IAP for in-app report unlocks, and Israel has no alternative-billing carve-out on either store. The web also captures SEO. Israeli law requires WCAG 2.0 AA (IS 5568) for public-facing sites and apps.

### Cited Findings
- **Apple:** IAP required for in-app unlocks; 3.1.3(e) does not apply. [V] — [Apple guidelines](https://developer.apple.com/app-store/review/guidelines/)
- **Accessibility law:** the service-accessibility regulations require internet services to meet IS 5568 at level AA. IS 5568 is based on WCAG 2.0. There are exemptions for heavy economic burden or small sites. Non-compliance exposes a business to lawsuits and fines; amounts not found. [S] — [BOIA](https://www.boia.org/blog/israels-digital-accessibility-laws-an-overview); [Kol Zchut exemptions](https://www.kolzchut.org.il/he/פטור_מחובת_הנגשה_לאתרי_אינטרנט_ואפליקציות); [SII standard page](https://www.sii.org.il/lobby/standardization/standard-page?id=6751); [gov.il IS 5568-2 (Sept 2023)](https://www.gov.il/BlobFolder/legalinfo/israeli_accessibility_standards_pdf/he/sitedocs_si-5568-2-september-2023.pdf)
- **Levi Itzhak ships free iOS and Android apps,** so competitors use apps for engagement and lead generation, not paid unlocks. [S] — [App Store](https://apps.apple.com/app/id1478184705)

### Inferences
- [E] A PWA or web app first, with a free companion app later (alerts, garage, saved cars) that does not sell reports in-app. That is a "consumption-only" style app; check Google's rules on that.
- [E] Budget for an accessibility audit and an accessibility statement (הצהרת נגישות) from launch.

### Gaps
- Israel-specific mobile-vs-desktop traffic share for car search: not found.

---

## 7. Infrastructure to archive government data

### Takeaway
[E] Archiving the gov.il/CKAN vehicle datasets is cheap: tens of dollars a month. Engineering time, not hosting, is the cost driver.

### Cited Findings
- The gov.il vehicle-history datasets exist and are public [S] — [gov.il](https://www.gov.il/he/Departments/DynamicCollectors/private_vehicle_history_1). Dataset sizes were not measured this session.

### Inferences [E]
- Assumptions: the vehicle registry is a few million rows and about 1–3 GB raw CSV; monthly full snapshots compress to about 0.3–1 GB as Parquet; daily diffs are smaller.
- Object storage (S3/R2-class, about $0.015–0.023 per GB-month, from my knowledge) gives under 50 GB after 3 years, which is under $2/month.
- A managed Postgres for serving (small instance) is about $25–100/month. A scheduler, compute and CDN are about $10–50/month.
- Total: about $50–200/month at early scale. Egress or CDN rises with traffic.
- The most valuable feature is diffing snapshots: ownership-change dates, odometer jumps or rollbacks, and status changes. Its value compounds, so start archiving on day 1.

### Gaps
- Actual dataset sizes and update frequency were not verified this session.

---

## 8. Dependency risk (Google, Meta, app stores)

### Takeaway
[E] Concentration risk is high. Search (organic and paid) is the main demand channel and Google costs are rising. App stores take 15–30% with no Israeli carve-out. Mitigate with B2B and partner channels and direct relationships (email, WhatsApp opt-in, saved-car alerts).

### Cited Findings
- Google Ads CPC rose about 13% year over year in 2025, and 87% of industries saw increases [S] — [Search Engine Land](https://searchengineland.com/google-ads-costs-rising-but-conversion-rates-improved-in-2025-477927)
- No alternative billing for Israel on Google Play (Israel not in the listed markets) [S] — [Google Play user choice billing](https://developer.android.com/google/play/billing/user-choice?hl=he); IAP is mandatory for in-app unlocks on iOS [V] — [Apple](https://developer.apple.com/app-store/review/guidelines/)
- carVertical's B2B line grew faster than its total revenue in 2024–2025 (101% and 83% vs 40% total in 2025) [S] — [carVertical blog](https://www.carvertical.com/en/blog/carvertical-revenue-growth)

### Inferences
- [E] Plan a dealer, garage and leasing B2B tier early. It diversifies away from Google and avoids app-store fees.
- [E] AI search answers that pull from gov.il data could cut organic clicks for basic plate lookups. Proprietary historical data is the hedge.

### Gaps
- Meta and Facebook-group reach and cost for Israeli car buyers: not found.
