# ScraperAPI vs ScrapingBee: What $49 Buys on Each, Which Targets Flip the Math, and How to Size Your Plan (Plan Table + Per-1,000-Page Costs)

Both entry plans cost $49 a month, and both vendors publish credit multipliers that decide what you actually pay. Those multipliers move in opposite directions. ScraperAPI bills 11 credits for a JavaScript-rendered page and 5 for an Amazon product page. ScrapingBee bills 5 credits to render and 75 for its stealth proxy tier. On a plain HTML page the two are within a rounding error of each other.

The rule worth carrying into a purchase decision: heavy Amazon, Walmart or eBay work, plus anything behind Cloudflare, DataDome or PerimeterX, goes to ScraperAPI; bulk plain pages, ordinary rendered pages and Google SERPs are cheaper on ScrapingBee. The rest of this piece is the plan table, the per-1,000-page arithmetic behind that rule, and the feature gaps that never show up on a pricing page.

> **Quick pick**
> - **Testing or a small job:** ScraperAPI Hobby at $49/month. 100,000 credits is 9,000 rendered pages, 20,000 Amazon pages or 4,000 Google SERPs, which is enough to measure your real credit burn before committing.
> - **Production Amazon, Walmart or eBay scraping:** Business at $299/month, 3,000,000 credits, or 600,000 Amazon product pages.
> - **Mostly static pages, normally rendered pages, or you need screenshots and scripted clicks:** ScrapingBee's per-page rate is lower and its $49 tier carries more credits.
>
> 👉 [See the current ScraperAPI plans and credit allowances](https://www.scraperapi.com/?fp_ref=coupons)

## ScraperAPI plans, credit for credit

ScraperAPI sells six monthly tiers, and every one takes 10% off on annual billing. Credits are the only currency; the dollar price per credit falls from $0.49 per 1,000 on Hobby to roughly $0.09 per 1,000 on Advanced.

| Plan | Monthly price | Credits per month | Rendered pages (11 credits each) | Start |
| --- | --- | --- | --- | --- |
| Hobby | $49 | 100,000 | ~9,000 | [Start Hobby](https://www.scraperapi.com/?fp_ref=coupons) |
| Startup | $149 | 1,000,000 | ~90,900 | [Start Startup](https://www.scraperapi.com/?fp_ref=coupons) |
| Business | $299 | 3,000,000 | ~272,700 | [Start Business](https://www.scraperapi.com/?fp_ref=coupons) |
| Scaling | $475 | 5,000,000 | ~454,500 | [Start Scaling](https://www.scraperapi.com/?fp_ref=coupons) |
| Professional | $975 | 10,500,000 | ~954,500 | [Start Professional](https://www.scraperapi.com/?fp_ref=coupons) |
| Advanced | $1,975 | 21,500,000 | ~1,954,500 | [Start Advanced](https://www.scraperapi.com/?fp_ref=coupons) |

Two details matter more than the headline price. Annual billing takes 10% off every tier, so Hobby works out to $44.10/month, and you receive the full year's credits upfront with the option to renew early for a fresh batch. Overage works differently by tier: on Hobby through Business the fallback is a pause or an opt-in auto-upgrade to the next plan, while pay-as-you-go past your allowance, at a fixed per-credit rate and a spending cap you set, opens up from Scaling upward.

There is also a free plan worth knowing about before you pay anything. It gives you 1,000 credits a month with 5 concurrent connections, and the first seven days after signup raise that to 5,000 so you can test at something closer to production scale. Paid plans carry a 7-day no-questions-asked refund.

👉 [Run the free credits against your own target list first](https://www.scraperapi.com/?fp_ref=coupons)

## The credit multiplier is the price

Four workloads priced in dollars, monthly billing, using each vendor's own credit rules. The workloads assume commonly cited volumes rather than any single customer's traffic.

| Workload | ScrapingBee | ScraperAPI |
| --- | --- | --- |
| 500,000 plain static pages | $99 Startup | $149 Startup |
| 100,000 rendered pages, ordinary sites | $99 Startup (500,000 credits) | $299 Business (1,100,000 credits) |
| 1,000 keywords tracked daily on Google, top 10 | $99 Startup (450,000 credits) | $149 Startup (750,000 credits) |
| 200,000 rendered pages behind Cloudflare | $1,599 Enterprise (15,000,000 credits) | $475 Scaling (4,200,000 credits) |

The Google row confuses people, so the arithmetic is worth spelling out. One keyword means one SERP request, and a SERP request returns the top 10 results. At 1,000 keywords a day, ScraperAPI charges 25 credits each, which is 25,000 credits a day and 750,000 a month. ScrapingBee charges 15 credits for a Google URL, giving 450,000 a month. Neither number is close to the number of keywords, and that is the point.

The Cloudflare row works the same way. ScraperAPI bills 11 credits for rendering (1 base plus 10) and adds 10 more to bypass Cloudflare, so 200,000 pages consume 4,200,000 credits. ScrapingBee needs its stealth proxy tier at 75 credits a page, which lands the same job at 15,000,000 credits and an enterprise contract.

Expressed per 1,000 pages at the Business tier, an Amazon product page costs $0.50 on ScraperAPI against $0.83 on ScrapingBee. A Cloudflare-protected page without rendering costs $1.10 against $6.23. The reverse holds on ordinary rendered pages at the entry tier: $5.39 per 1,000 on ScraperAPI against $0.98 on ScrapingBee, a gap of more than five times.

ScraperAPI bills successful requests. Failed and blocked requests generally don't consume credits, which matters when your target mix includes sites that intermittently refuse connections.

👉 [Price your own target list against ScraperAPI's current tiers](https://www.scraperapi.com/?fp_ref=coupons)

## What each one is actually good at

Neither vendor sells raw proxies. You post a URL to an endpoint and get HTML or JSON back with rotation, retries and CAPTCHA handling done for you. If you want a list of IPs and a username and password to plug into your own crawler, both are the wrong purchase.

| Capability | ScraperAPI | ScrapingBee |
| --- | --- | --- |
| Session persistence | 15 minutes | 5 minutes |
| Webhooks / async jobs | Yes / yes | No / no |
| Scheduled runs without code | DataPipeline, up to 10,000 URLs, keywords or ASINs per run | No |
| Screenshots | No | Full page and elements |
| Custom JS before capture | No | `js_scenario`, up to 40 seconds |
| Structured SERP and Amazon JSON | Yes | No, you parse the HTML |
| SDK languages | Python, Node, Ruby, PHP | Python, Node |

The session gap decides multi-step workflows. A 15-minute hold on the same IP covers a login followed by a paginated crawl without re-authenticating; five minutes often doesn't. ScraperAPI's session control pairs with a per-request choice of proxy tier, which is more predictability than most teams need and exactly what some do.

ScrapingBee's edge sits on the other side of the request. Custom JavaScript scenarios let you scroll, wait and click a next-page link before the capture, and the extraction rules return structured fields instead of raw HTML. Screenshots come back as images. If your pipeline needs a rendered page or a picture of one, ScraperAPI doesn't do it and you'd be stitching in a second tool.

## Where the marketing numbers fall apart

Every success-rate percentage you see quoted for either vendor is a marketing claim. Neither company publishes independently audited uptime or success-rate figures, so 99.99% and 98% and 62% and 44% are all unfalsifiable in public.

What's defensible is narrower. On moderately protected e-commerce targets, the two land in a similar range on standard requests. ScrapingBee's real headless Chrome gives it a slight edge on JavaScript-heavy sites with hard bot detection, because it runs a full browser rather than a lighter fetch layer. On plain server-rendered pages that gap mostly disappears, and ScraperAPI tends to be faster on non-JS requests since there's no browser to spin up.

Run your own sample against both free tiers before you trust any published benchmark, including this one.

## Who shouldn't buy either

If you need a raw residential or mobile IP pool to route through your own tooling, with ASN-level or city-level control, neither product fits and a dedicated proxy network is the correct purchase. The same applies if you need to hold a specific IP for hours, or if your requests must originate from a fixed set of addresses you manage yourself.

A second group: anyone whose monthly volume sits under a few hundred thousand pages and who already runs scheduling and storage in Airflow or a queue worker. ScraperAPI slots in cleanly as a fetch layer in that setup, and the free plan plus a $49 month will tell you whether it holds up.

## FAQ

**Is the $49 Hobby plan enough to start?**
For a prototype, yes. 100,000 credits translates to 9,000 rendered pages, 20,000 Amazon product pages, 4,000 Google SERPs or 100,000 plain pages. If your crawl needs more than about 300 rendered pages a day, you'll be upgrading within weeks.

**How are rendered pages charged?**
ScraperAPI adds 10 credits to the base cost, so a rendered page is 11 credits. ScrapingBee charges 5 credits for rendering on a classic proxy, and 25 when rendering runs over a premium proxy.

**Why does one Google search cost 25 credits?**
Because the vendor prices guaranteed SERP access as a premium target, the same way LinkedIn sits at 30 credits and Amazon at 5. A daily rank-tracking job across 1,000 keywords is 750,000 credits a month on ScraperAPI, which is why it lands on Startup rather than Hobby.

**Do failed requests cost credits?**
ScraperAPI bills per successful request, and blocked or failed attempts generally don't consume the balance. Check the other vendor's policy separately if your targets block aggressively.

**Is annual billing worth it?**
10% off is real money at the Professional and Advanced tiers, and the credits arrive upfront for the year. The risk is committing before you know your multiplier mix, so buy monthly for one cycle, measure your actual credits per target, then switch.

## Picking between them

Match the vendor to your target list, then to volume.

Amazon, Walmart, eBay or anything behind Cloudflare, DataDome or PerimeterX: ScraperAPI. Start on Hobby to measure the burn, move to Business when the numbers are predictable and you need 3,000,000 credits.

Plain HTML at volume, ordinary JavaScript-rendered pages, Google SERPs, or a pipeline that needs screenshots and scripted clicks: ScrapingBee's per-page rates are lower on all four.

Two things to confirm on the plan page before you pay. First, the concurrency cap on your chosen tier, since both vendors have adjusted thread limits over time and the cap decides how long a full crawl takes. Second, whether the countries your targets sit in are covered by the geo settings on that tier, because finer country targeting is reported to start at Business and above, and getting this wrong means re-running a crawl you already paid for.

👉 [Compare ScraperAPI's tiers and pick the one that matches your targets](https://www.scraperapi.com/?fp_ref=coupons)
