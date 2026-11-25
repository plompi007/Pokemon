# Primary-source check of the competitor, market and economics claims (Israel vehicle-report market)

Date checked for every item: **2026-11-25**.
Labels: **[VERIFIED-PRIMARY]** means I read it in the page's own HTML in this session. **[SECONDARY]** means a search-engine snippet or summary only. **[NOT FOUND]** and **[CONTRADICTION]** are used where they apply. "(my estimate)" marks my own inference.

**Access results this session.** The network allowlist was opened, but several sites sit behind bot protection. I did **not** try to get around it (no spoofed browser headers, no challenge solving):
- www.carzone.co.il: every path (/car-report, /slika, /about, /terms, /privacy, /order-cancel, robots.txt) returned **HTTP 429 "Vercel Security Checkpoint"**. This is a JavaScript bot challenge. WebFetch failed separately with DNS ENOTFOUND.
- www.autoboom.co.il, www.find-car.co.il, levi-itzhak.co.il: **HTTP 403, Cloudflare "Sorry, you have been blocked"**. The bare autoboom.co.il (without www) did not connect at all.
- www.yad2.co.il/price-list: **Radware "Verifying your browser"** page.
- similarweb.com/website/<domain>/: **HTTP 202 with an empty body** (a challenge). The public "top websites" category page did load.
- Loaded normally: check-car.co.il, cartube.co.il, carvertical.com, calcalist.co.il, globes.co.il, auto.co.il.

To verify Carzone, Autoboom, Find-Car, Levi Itzhak and Yad2, someone has to open them in a real browser by hand. Changing the network allowlist will not help, because the blocks come from the sites' own bot protection.

## Q1. Carzone: what the report contains (free vs paid), prices and packages, operator, data sources, B2B

### Takeaway
I could not fetch Carzone. It returns 429 from its Vercel bot checkpoint, so **nothing about Carzone was upgraded to verified-primary**. Current search snippets of its own pages back up the earlier notes: 2 free reports on sign-up, the listed report contents, no clearing-center data, and a 12 ₪ clearing report from which Carzone says it takes no commission. They also show a separate **lien/attachment check page** (/car-report/liens-check). The exact paid price, the packages, the legal entity and the terms are still **[NOT FOUND]**.

### Cited Findings
- All Carzone URLs returned HTTP 429 "Vercel Security Checkpoint" when fetched directly on 2026-11-25. — [carzone.co.il/car-report](https://www.carzone.co.il/car-report) (fetch attempt; no content)
- The homepage offers "register and get 2 free reports for a plate of your choice". **[SECONDARY]** (search summary of Carzone's own page, 2026-11-25) — [carzone.co.il](https://carzone.co.il/)
- Report contents per its own page: ownership history, originality, past ads with photos, test reports, mileage "including fakes", price list, theft. It claims to have flagged suspected mileage tampering in "over 70 thousand vehicles". **[SECONDARY]** — [carzone.co.il/car-report](https://www.carzone.co.il/car-report), [carzone.co.il](https://carzone.co.il/)
- Carzone says the Ministry of Transport does not publish full extended data (mileage reports, ownership changes) for some older cars, mainly those over about 8 years old. **[SECONDARY]** — [carzone.co.il/car-report](https://www.carzone.co.il/car-report)
- The report does not include a check with the insurers' clearing center. Carzone points users to a 12 ₪ report bought directly from "מרכז הסליקה של חברות ביטוח בע"מ" and states it **takes no commission** on that report. **[SECONDARY]** — [carzone.co.il/slika](https://www.carzone.co.il/slika)
- **New:** Carzone has a page "בדיקת שעבוד, משכון ועיקול לרכב לפני קנייה" (lien, pledge and attachment check before purchase). Its price and whether it is a paid product or a guide were not visible. **[SECONDARY: title only]** — [carzone.co.il/car-report/liens-check](https://www.carzone.co.il/car-report/liens-check)
- Carzone says about 15,000 vehicles a year have their mileage tampered with. This is a self-claim, not an official statistic. **[SECONDARY]** — [carzone.co.il/news/kmTampering](https://www.carzone.co.il/news/kmTampering/)
- Price per report, packages and 12-month validity: **[NOT FOUND in primary]**. Market_demand.md cites the order-cancellation page for "packages valid 12 months". I could not re-check this (429).
- Operator / legal entity / founders: **[NOT FOUND]**. The /about page exists but could not be read (429).
- Dealer / B2B product ("Carzone Pro" or similar): **[NOT FOUND]**.
- Terms of use, anti-scraping clauses and data-source statements: **[NOT FOUND]** (429).

### Inferences
- (my estimate) The site is served through Vercel with bot protection turned on. This fits the earlier inference that Carzone protects its listings archive against scraping.
- (my estimate) The "no commission" statement on the clearing report suggests that Carzone does not currently earn from the clearing-center upsell. The upsell is a referral, not a revenue line.

### Gaps
- All Carzone pricing, entity, terms and B2B questions need a manual browser visit to /car-report (the purchase flow up to payment, without paying), /about, /terms and /order-cancel.

## Q2. Other private report sites: Check-Car, Cartube, Autoboom, Find-Car, Carstop

### Takeaway
**Check-Car and Cartube are verified-primary as free, unlimited, gov-data-only lookups.** Neither shows any price or paywall. Autoboom and Find-Car were blocked by Cloudflare, so their earlier prices stay unverified. A search snippet confirms that Autoboom locks some sections behind a "full report".

### Cited Findings
- **Check-Car (check-car.co.il)** [VERIFIED-PRIMARY]: "free detailed report" by plate or VIN, also for motorcycles and trucks. Contents: ownership history and number of hands, original ownership type (leasing, taxi), current ownership, road date, licence validity, last-test mileage, open recalls, "שווי שימוש" (2010+), number of units of the model on the road since 2018, disabled badge, pollution grade, safety equipment, tyres, technical data, and "עבר כלי הרכב, תו נכה לרכב וטוטאל לוס". It says it cross-references several databases "based on MoT data", and that the report is "completely free, without payment" with "no limit on the number of searches". — [check-car.co.il](https://www.check-car.co.il/)
- **Cartube (cartube.co.il)** [VERIFIED-PRIMARY]: "full report" by plate. Contents: maker, model, trim, year and road date; ownership history (private, leasing, rental, company, dealer; for cars on the road from 2017); last-test mileage, licence validity and changes; open recalls, list price, specs and safety equipment. "All data comes from government databases (data.gov.il) and is updated daily. The report does not include identifying details of owners." No price, paywall or payment wording appears on the page, so it is free. Cartube's main business is car news and new-car price lists, which suggests ad and lead revenue (my estimate). — [cartube.co.il/איתור-מספר-רכב](https://www.cartube.co.il/%D7%90%D7%99%D7%AA%D7%95%D7%A8-%D7%9E%D7%A1%D7%A4%D7%A8-%D7%A8%D7%9B%D7%91)
  - This **corrects** competitors.md, which listed "Cartube price: not found". The lookup is free.
- **Autoboom**: Cloudflare 403. A search snippet of its English check-car pages says ownership history is shown for vehicles from 2017 onward and "some sections are locked behind access to the full report". No price appeared. It also runs a "Find" service: turnkey car selection, new-model selection and on-site inspection. **[SECONDARY]** — [autoboom.co.il/en/magazine/car-selection](https://autoboom.co.il/en/magazine/car-selection), [autoboom.co.il/en/check-car/82556103](https://autoboom.co.il/en/check-car/82556103). The earlier claim of 55 ₪ for one report and 25 ₪ per report in a 10-pack is **still unverified**.
- **Find-Car**: Cloudflare 403. The earlier claim of a lien and stolen-car report at 280 ₪ (140 ₪ for subscribers) is **still unverified**. — [find-car.co.il/home](https://www.find-car.co.il/home) (fetch blocked)
- **New name surfaced:** "קארסטופ" (Carstop), described as a site that makes data on second-hand cars accessible. Not investigated. **[SECONDARY: title only]** — [queenoftheroad.co.il](https://www.queenoftheroad.co.il/%d7%9c%d7%a4%d7%a0%d7%99-%d7%94%d7%a8%d7%9b%d7%99%d7%a9%d7%94-%d7%a7%d7%90%d7%a8%d7%a1%d7%98%d7%95%d7%a4-%d7%90%d7%aa%d7%a8-%d7%9c%d7%94%d7%a0%d7%92%d7%a9%d7%aa-%d7%9e%d7%99%d7%93%d7%a2-%d7%a2%d7%9c/)

### Inferences
- (my estimate) Two well-built free sites already package everything that comes from MoT open data: hands, ownership type, test mileage, recalls, list price and specs. Check-Car even claims total-loss and disabled-badge flags. A paid product therefore cannot charge for gov-data aggregation. Paid value has to come from data that is not on data.gov.il: the listings archive and photos (Carzone's hook), the clearing-center accident history, lien and attachment status, and service records.

### Gaps
- Autoboom and Find-Car price lists and report contents (blocked). Carstop details.

## Q3. Levi Itzhak: consumer and business prices, API or B2B

### Takeaway
The site was blocked by Cloudflare, so **nothing about Levi Itzhak's prices was verified**. **One correction:** the "45 ₪ per printed issue" figure and the Yad2 "delusional prices" quote both come from a **Globes article of 9 January 2011**. That is 15 years old and must not be presented as current.

### Cited Findings
- Globes article "לוי יצחק: 'המחירים במחירון יד2 הזויים; נכשלו שם באמינות'" by Itai Rom, dated **09.01.2011** [VERIFIED-PRIMARY, header and lead only; the rest is paywalled]. It says Levi sells his price list "at the not-at-all-modest price of 45 ₪". The trigger was Yad2's free online price list, which "from last month is also distributed" in print. — [globes.co.il did=1000613392](https://www.globes.co.il/news/article.aspx?did=1000613392)
- The earlier claims of an 840 ₪ annual printed subscription and online tiers of 10 ₪ per day, 25 ₪ per week and 50 ₪ per month: **unverified** (levi-itzhak.co.il returned 403).
- An API or B2B offering: **[NOT FOUND]**.
- Search summaries of iCar say Levi Itzhak's price list has been the benchmark for banks, insurers and private deals since the 1970s, and that it runs about 20–30% above current market price. **[SECONDARY]** — [icar.co.il obituary](https://icar.co.il/חדשות_רכב/הלך_לעולמו_לוי_יצחק,_האיש_מאחורי_מחירון_הרכב_המשפיע_במדינה/)

### Gaps
- Current consumer, dealer and API prices need a manual visit to levi-itzhak.co.il.

## Q4. Yad2: paid vehicle report or plate check; price list

### Takeaway
I could not verify this, because Yad2 is behind Radware bot protection. Searches found **no evidence of a paid Yad2 vehicle report**. The Yad2 price list has been free since about December 2010, per Globes 2011.

### Cited Findings
- yad2.co.il/price-list returned the Radware "Verifying your browser before proceeding" page. — [yad2.co.il/price-list](https://www.yad2.co.il/price-list) (fetch blocked)
- Yad2's free internet price list had begun print distribution in about December 2010 [VERIFIED-PRIMARY, lead]. — [Globes 09.01.2011](https://www.globes.co.il/news/article.aspx?did=1000613392)
- A search for "יד2 דוח רכב לפי מספר רישוי בתשלום" (Yad2 paid plate report) returned only gov.il, Cartube and Carzone pages. No Yad2 report product appeared. **[NOT FOUND]** — search results 2026-11-25

### Gaps
- Whether Yad2 listings show plate data or sell a report.

## Q5. carVertical: prices and Israel coverage

### Takeaway
[VERIFIED-PRIMARY] carVertical has **no Israel locale or pricing market**. Its pricing page links about 45 country versions (EU, UK, Balkans, Ukraine, Moldova, US-Spanish, Mexico, Australia, New Zealand, South Africa, UAE), and Israel is not among them. Its prices are loaded dynamically (shown as "loading"), so the exact current figures could not be read.

### Cited Findings
- The pricing page shows "loading … VAT may apply". Price figures are not in the HTML, and the default currency config is "EUR". — [carvertical.com/en/pricing](https://www.carvertical.com/en/pricing) [VERIFIED-PRIMARY]
- Locale pricing pages linked: ae, at, au, ba, be, bg, ch, cz, de, dk, es, et, fi, fr, gb, gr, hr, hu, ie, it, lt, lv, md, mx, nl, no, nz, pl, pt, ro, rs, se, si, sk, ua, us/es, za. There is no "il". carvertical.com/il returns **404**. "Israel" appears only in a generic country dropdown. — [carvertical.com/en/pricing](https://www.carvertical.com/en/pricing), [carvertical.com/il](https://www.carvertical.com/il) (404) [VERIFIED-PRIMARY]
- carVertical says its data comes from "1000+ international databases" (registries, insurers, police, garages), that each data request has a cost, "which is why our reports aren't provided for free", and that it offers API integration for business. — [carvertical.com/en/pricing](https://www.carvertical.com/en/pricing) [VERIFIED-PRIMARY]
- The earlier claim of "$29.99 per report / $16.99 each in a 3-pack" is **unverified**, because prices load dynamically.

### Inferences
- (my estimate) carVertical is not currently a direct competitor in Israel. Its model is a European benchmark for "paid because each source costs money", unlike Israel's free gov-data wrappers.

## Q6. Similarweb traffic for carzone, yad2, levi-itzhak, autoboom

### Takeaway
The per-site Similarweb pages were blocked (HTTP 202 challenge), so **I have no Similarweb visit numbers or traffic-source splits**. Similarweb's public category page for "Automotive Industry – Israel" (October 2026) ranks icar.co.il, auto.co.il, toyota.co.il, wheel.co.il and geely.co.il as the top 5. Carzone is not in the visible top 5 (the rest is paywalled).

### Cited Findings
- Similarweb, "Top Automotive Industry Websites Ranking in Israel", October 2026, last updated 1 Nov 2026: 1 icar.co.il, 2 auto.co.il, 3 toyota.co.il, 4 wheel.co.il (up 3), 5 geely.co.il (up 4). The full list is behind a trial. — [similarweb.com top-websites/israel/vehicles/automotive-industry](https://www.similarweb.com/top-websites/israel/vehicles/automotive-industry/) [VERIFIED-PRIMARY]
- carzone.co.il per-site page: HTTP 202 with an empty body. **[NOT FOUND]** — [similarweb.com/website/carzone.co.il](https://www.similarweb.com/website/carzone.co.il/)
- Other tools, from search summaries only: Ahrefs puts carzone.co.il at about 143K visits in June 2025, 99% from Israel. Semrush shows about 162.1K in October 2025 with an average session of 8:34. A Semrush competitor view in November 2025 shows about 157.6K visits and a 68.3% bounce rate. **[SECONDARY]** — [ahrefs.com/websites/carzone.co.il](https://ahrefs.com/websites/carzone.co.il), [tr.semrush.com carzone overview](https://tr.semrush.com/website/carzone.co.il/overview), [semrush auto.co.il competitors](https://www.semrush.com/website/auto.co.il/competitors/)

### Gaps
- Similarweb visits and source split for carzone, yad2, levi-itzhak and autoboom. These need a logged-in Similarweb session or a manual browser visit.

## Q7. Used-car ownership-transfer figures (2023–2025) and the 714k contradiction

### Takeaway
[VERIFIED-PRIMARY] Calcalist (Tomer Hadar, 20.01.2026), citing exclusive MoT data, gives **1,316,302 used-car ownership transfers in 2025, against 1,293,862 in 2024 (+1.7%) and 1,121,322 in 2023**. That settles the year-label contradiction: 2024 is 1.29M and 2025 is 1.32M. No private, dealer or leasing breakdown is published. The only partial breakdowns are by model year and fuel type. **The ~714k figure could not be traced to any primary source.** It conflicts with Calcalist's 1.12M for 2023 and should be dropped or flagged.

### Cited Findings
- "Last year [2025] 1,316,302 used-car ownership transfers were carried out in Israel. For comparison, in 2024 … 1,293,862 … a moderate rise of 1.7% … in 2023, 1,121,322 ownership transfers were carried out." — [Calcalist, "בלון או מגמה? שוק החשמליות המשומשות מתעורר", 20.01.26](https://www.calcalist.co.il/local_news/car/article/sjwlh3hhzg) [VERIFIED-PRIMARY]
- The same article gives 64,342 transfers of **model-2025** cars in 2025. Industry estimates attribute most of them to "יד ראשונה אפס ק"מ" cars that dealers or leasing companies bought new and resold. Calcalist notes the figure "is not absolute". — same source [VERIFIED-PRIMARY]
- Used EV transfers were **51,778** in 2025 against **32,814** in 2024. These are exact figures; the earlier notes said "over 51k" and "about 33k". — same source [VERIFIED-PRIMARY]
- Definition: Calcalist defines "העברת בעלות" as **any** change of hands recorded in licensing-office computers, including a brand-new car going from first to second hand. So the series counts transfer events and includes dealer and leasing legs. — [Calcalist, "יותר אפס קילומטר, פחות עסקאות", 15.07.25](https://www.calcalist.co.il/local_news/car/article/bypctuqlxx) [VERIFIED-PRIMARY]
- H1 2025: **636,971** transfers against **638,760** in H1 2024. Model-2025 transfers in H1 2025: **20,715**, against 18,924 model-2024 cars in H1 2024. Calcalist assumes these were mostly importer-to-leasing sales. — same source [VERIFIED-PRIMARY]
- The 714k figure: no primary source was found. A search returned older MoT figures cited by Walla: **701,442 transfers in 2010, 685,830 in 2009 and 632,179 in 2008**. 714k is in the range of that early-2010s series and is far below 2023–2025. **[SECONDARY]** — [cars.walla.co.il/item/1796837](https://cars.walla.co.il/item/1796837). The Ken Research and ynetnews citations for 714k were not re-checked (ynetnews.com is not on the allowlist), and they are **not reliable** for 2023/2024.
- Breakdown by private, dealer and leasing channel: **[NOT FOUND]** in any of these articles.

### Inferences
- (my estimate) The series grew from about 0.70M (2010) to 1.12M (2023) and 1.29–1.32M (2024–2025). The jump from 2023 to 2024 (+15%) is large. It may reflect the "0 km" resale wave and a bigger fleet, but I did not verify the cause.
- (my estimate) The market_demand.md estimate of 0.7–1.0M end-buyer purchases is still a reasonable estimate. But it should no longer lean on the 714k figure as a "unique vehicles" anchor, because that figure looks like a stale number from about 2010–2011.

### Gaps
- The CBS and data.gov.il tables needed to split transfers by ownership type were not accessed.

## Q8. Clearing-center price, press coverage of report companies, failures

### Takeaway
The "10 ₪" clearing-center price comes from an **old auto.co.il article**. Its own text says data reaches back to "2011 at least", which suggests it was written around 2018. Carzone's 12 ₪ (from a snippet) is the more current figure. I found no Calcalist, Globes or ynet article about vehicle-report companies, price drops or failures.

### Cited Findings
- auto.co.il, "שירות חדש: מידע על עבר ביטוחי לרכב משומש" [VERIFIED-PRIMARY]: the service is run by "מרכז הסליקה של חברות ביטוח", a subsidiary of the Israel Insurance Association. It covers property-damage claims paid, insurer, damage type including theft, depreciation rate and claim status, going back up to 7 years ("today, 2011 at least"). It costs **10 ₪**, and **only the vehicle owner** can order it. — [auto.co.il/article/129901-local-news](https://www.auto.co.il/article/129901-local-news)
- Carzone's current page gives **12 ₪** for the same report. **[SECONDARY]** — [carzone.co.il/slika](https://www.carzone.co.il/slika). This is a price change over time, not a conflict.
- Calcalist, Globes or ynet articles on vehicle-report companies, price drops or shutdowns: **[NOT FOUND]** in targeted searches. The only related item is still the 2023 TheMarker article seen by title only (see competitors.md).

### Gaps
- Failed or closed report services: still none documented.

## Summary of status changes vs earlier notes

### Takeaway
Upgraded to verified-primary: transfer figures for 2023, 2024, 2025 and H1 2024/2025; EV transfer figures; Check-Car and Cartube contents and free status; carVertical's lack of an Israel market; the dates of the Globes Levi/Yad2 article and the auto.co.il clearing article. Corrections: Cartube is free; the 714k figure is untraceable and looks stale; Levi's 45 ₪ and the Yad2 attack date from 2011; clearing at 10 ₪ is old. Still unverified because of bot protection: all Carzone, Autoboom, Find-Car, Levi Itzhak, Yad2 and Similarweb per-site figures.

### Cited Findings
- See the citations under Q1–Q8 above. Each line carries its source URL, checked 2026-11-25.

### Inferences
- (my estimate) The competitive floor is "free and unlimited" (Check-Car, Cartube, apps). Carzone is the only identified player monetising history reports beyond gov data, plus possibly Autoboom and Find-Car (unverified).

### Gaps
- A manual browser session is needed for carzone.co.il, autoboom.co.il, find-car.co.il, levi-itzhak.co.il, yad2.co.il and similarweb.com per-site pages. Their bot protection (Vercel, Cloudflare, Radware) blocks automated fetching even with the network opened.
