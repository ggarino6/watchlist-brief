# Evaluation test set

Fill this in after every refresh, before you publish. The agent is the system under test.
You are the grader. Nothing here is automated on purpose: the point is to decide, with a
source you trust, whether the agent told you the truth.

**Ground truth sources.** Pick one and use the same one every time, so your scores are
comparable week to week:

- Prices: Google Finance (google.com/finance), Yahoo Finance, or your brokerage app.
- News: the article itself. Open the link. Check the date on the page.
- Calendar: the company's investor relations page (search "TICKER investor relations
  events"), or the Fed's own meeting calendar for FOMC dates.

Refresh date: 2026-10-28    Grader: number-checker (agent)

Run note (2026-10-28): Google Finance would not open ("not supported on this device"), so
all ground-truth prices come from Yahoo Finance history pages, fetched about 10:14 ET.
Dashboard prices come from StockAnalysis; I did not use it as ground truth.

## A. Prices (one row per ticker)

Pass if the dashboard's last price is within $0.10 of the ground truth for the same day
and the same price type (close vs intraday). If the agent recorded an intraday price,
compare against the intraday price at about the same time; do not compare it to a close.

| Ticker | Date shown | Price type shown | Dashboard price | Ground truth price | Source you used | Pass / Fail |
|---|---|---|---|---|---|---|
| XOM | 2026-10-21 | close | 178.09 | 178.09 | Yahoo Finance https://finance.yahoo.com/quote/XOM/history/ | Pass |
| XOM | 2026-10-22 | close | 178.23 | 178.23 | Yahoo Finance https://finance.yahoo.com/quote/XOM/history/ | Pass |
| XOM | 2026-10-23 | close | 183.21 | 183.21 | Yahoo Finance https://finance.yahoo.com/quote/XOM/history/ | Pass |
| XOM | 2026-10-26 | close | 184.54 | 184.54 | Yahoo Finance https://finance.yahoo.com/quote/XOM/history/ | Pass |
| XOM | 2026-10-27 | close | 179.91 | 179.91 | Yahoo Finance https://finance.yahoo.com/quote/XOM/history/ | Pass |
| XOM | 2026-10-28 10:05 ET | latest (intraday) | 180.97 | 181.64 at 10:14 ET (history row 181.68) | Yahoo Finance https://finance.yahoo.com/quote/XOM/history/ | Fail (0.67 off; quote is 9 min later, so partly time skew, but not verifiable within $0.10) |
| CVX | 2026-10-21 | close | 226.78 | 226.78 | Yahoo Finance https://finance.yahoo.com/quote/CVX/history/ | Pass |
| CVX | 2026-10-22 | close | 226.68 | 226.68 | Yahoo Finance https://finance.yahoo.com/quote/CVX/history/ | Pass |
| CVX | 2026-10-23 | close | 233.21 | 233.21 | Yahoo Finance https://finance.yahoo.com/quote/CVX/history/ | Pass |
| CVX | 2026-10-26 | close | 232.01 | 232.01 | Yahoo Finance https://finance.yahoo.com/quote/CVX/history/ | Pass |
| CVX | 2026-10-27 | close | 228.23 | 228.23 | Yahoo Finance https://finance.yahoo.com/quote/CVX/history/ | Pass |
| CVX | 2026-10-28 10:04 ET | latest (intraday) | 229.28 | 229.52 at 10:14 ET (history row 229.60) | Yahoo Finance https://finance.yahoo.com/quote/CVX/history/ | Fail (0.24 off; 10 min time skew, not verifiable within $0.10) |
| SHEL | 2026-10-21 | close | 105.36 | 105.36 | Yahoo Finance https://finance.yahoo.com/quote/SHEL/history/ | Pass |
| SHEL | 2026-10-22 | close | 105.80 | 105.80 | Yahoo Finance https://finance.yahoo.com/quote/SHEL/history/ | Pass |
| SHEL | 2026-10-23 | close | 108.18 | 108.18 | Yahoo Finance https://finance.yahoo.com/quote/SHEL/history/ | Pass |
| SHEL | 2026-10-26 | close | 106.91 | 106.91 | Yahoo Finance https://finance.yahoo.com/quote/SHEL/history/ | Pass |
| SHEL | 2026-10-27 | close | 104.78 | 104.78 | Yahoo Finance https://finance.yahoo.com/quote/SHEL/history/ | Pass |
| SHEL | 2026-10-28 10:03 ET | latest (intraday) | 105.18 | 105.14 at 10:13 ET (history row 105.18) | Yahoo Finance https://finance.yahoo.com/quote/SHEL/history/ | Pass |
| BP | 2026-10-21 | close | 49.85 | 49.85 | Yahoo Finance https://finance.yahoo.com/quote/BP/history/ | Pass |
| BP | 2026-10-22 | close | 50.05 | 50.05 | Yahoo Finance https://finance.yahoo.com/quote/BP/history/ | Pass |
| BP | 2026-10-23 | close | 51.32 | 51.32 | Yahoo Finance https://finance.yahoo.com/quote/BP/history/ | Pass |
| BP | 2026-10-26 | close | 50.53 | 50.53 | Yahoo Finance https://finance.yahoo.com/quote/BP/history/ | Pass |
| BP | 2026-10-27 | close | 48.93 | 48.93 | Yahoo Finance https://finance.yahoo.com/quote/BP/history/ | Pass |
| BP | 2026-10-28 10:04 ET | latest (intraday) | 49.37 | 49.45 at 10:14 ET (history row 49.44) | Yahoo Finance https://finance.yahoo.com/quote/BP/history/ | Pass (0.08 off, borderline) |
| COP | 2026-10-21 | close | 145.67 | 145.67 | Yahoo Finance https://finance.yahoo.com/quote/COP/history/ | Pass |
| COP | 2026-10-22 | close | 145.63 | 145.63 | Yahoo Finance https://finance.yahoo.com/quote/COP/history/ | Pass |
| COP | 2026-10-23 | close | 150.80 | 150.80 | Yahoo Finance https://finance.yahoo.com/quote/COP/history/ | Pass |
| COP | 2026-10-26 | close | 151.37 | 151.37 | Yahoo Finance https://finance.yahoo.com/quote/COP/history/ | Pass |
| COP | 2026-10-27 | close | 147.96 | 147.96 | Yahoo Finance https://finance.yahoo.com/quote/COP/history/ | Pass |
| COP | 2026-10-28 10:02 ET | latest (intraday) | 149.06 | 149.04 at 10:13 ET (history row 149.24) | Yahoo Finance https://finance.yahoo.com/quote/COP/history/ | Pass |

Note: all 25 closes match exactly. The only Fails are the XOM and CVX intraday "latest"
rows; Yahoo quotes were taken 9-10 minutes after the dashboard times, so a re-check at the
same minute could clear them. Total 28/30.

## B. Weekly change (one row per ticker)

The page computes this from the five closes. Pass if it is within 0.3 percentage points of
your own calculation: (last price minus the close five trading days earlier) divided by
that earlier close.

Your calculation uses the Oct 21 close and the Yahoo quote at about 10:14 ET on Oct 28.

| Ticker | Dashboard weekly change | Your calculation | Source | Pass / Fail |
|---|---|---|---|---|
| XOM | +1.6% ((180.97-178.09)/178.09) | +2.0% ((181.64-178.09)/178.09) | https://finance.yahoo.com/quote/XOM/history/ | Fail (0.4 pts off) |
| CVX | +1.1% | +1.2% ((229.52-226.78)/226.78) | https://finance.yahoo.com/quote/CVX/history/ | Pass |
| SHEL | -0.2% | -0.2% ((105.14-105.36)/105.36) | https://finance.yahoo.com/quote/SHEL/history/ | Pass |
| BP | -1.0% | -0.8% ((49.45-49.85)/49.85) | https://finance.yahoo.com/quote/BP/history/ | Pass (0.2 pts) |
| COP | +2.3% | +2.3% ((149.04-145.67)/145.67) | https://finance.yahoo.com/quote/COP/history/ | Pass |

Dashboard values are my recomputation of what the page shows from BRIEF (first close to latest.price).

## C. News grounding (one row per news item, three per ticker)

Open every link. Pass only if all four are true: the link opens, the headline matches the
article, the article date is within the last seven days, and the "why it matters" line is
supported by the article (not just plausible).

| Ticker | Headline (first few words) | Link opens | Headline matches | Dated within 7 days | "Why" is supported | Source | Pass / Fail |
|---|---|---|---|---|---|---|---|
| XOM | Shell, ExxonMobil JV Infineum exploring sale | Yes | Yes | Yes, article Oct 22 (BRIEF Oct 22 matches) | Mostly. Article: Infineum "has hired Bank of America to run a sale", targeting "about $8 billion". "Could bring Exxon cash" is the agent's inference, not stated. | https://www.tipranks.com/news/the-fly/shell-exxonmobil-jv-infineum-exploring-sale-ft-reports-thefly-news | Pass (inference noted) |
| CVX | (no news items; list is empty and the changelog says so) | n/a | n/a | n/a | n/a | n/a | not scored (0 items) |
| SHEL | Shell, ExxonMobil JV Infineum exploring sale | Yes | Yes | Yes, Oct 22 (matches) | Yes. Same article: owned 50:50 by Shell and ExxonMobil, target valuation about $8 billion. | https://www.tipranks.com/news/the-fly/shell-exxonmobil-jv-infineum-exploring-sale-ft-reports-thefly-news | Pass |
| BP | BP, Louisiana agree to Deepwater Horizon settlement payout | Yes | Yes | Yes, Oct 23 (matches) | Yes. "accelerated, lump-sum US$350 million payment"; Louisiana was to get $373 million in installments over seven years. | https://www.bnnbloomberg.ca/business/international/2026/10/23/bp-louisiana-agree-to-deepwater-horizon-settlement-payout-resolve-coastal-cases/ | Pass |
| COP | ConocoPhillips assumed with a Neutral at Piper Sandler | Yes | Yes | Yes, Oct 27 09:15 UTC (matches) | Yes. Neutral, $157 target, "heavy period of long-cycle investment", free cash flow inflection later. | https://www.tipranks.com/news/the-fly/conocophillips-assumed-with-a-neutral-at-piper-sandler-thefly-news | Pass |

Note: the XOM and SHEL rows are the same article. Only 4 news items exist, 1 per ticker
except CVX (0).

(Add rows as needed. Fifteen items is normal for five tickers.)

## D. Calendar (one row per event)

Pass if the event and its date appear on the source linked, and the date is in the future
relative to the refresh date.

| Ticker | Event | Date shown | Confirmed on source | Source | Pass / Fail |
|---|---|---|---|---|---|
| XOM | FOMC rate decision | 2026-10-28 | Yes: meeting listed Oct 27-28, 2026 (on/after asOf). The "2:00 PM ET" time is not on that page. | https://www.federalreserve.gov/monetarypolicy/fomccalendars.htm | Pass |
| XOM | Q3 2026 earnings | 2026-10-30 | Yes: company IR calendar "3Q 2026 Earnings Call", Fri Oct 30, 8:30 a.m. CT. Confirmed, not "expected". Event text still says "not confirmed on company page", which is now stale. | https://investor.exxonmobil.com/news-events/ir-calendar/detail/20261030-3q-2026-earnings-call | Pass |
| CVX | Q3 2026 earnings | 2026-10-30 | No. chevron.com investor pages returned HTTP 403 / certificate error (source unreachable). Only a third-party AI-generated aggregator (money365.market) shows Oct 30 11:00 ET. | https://www.chevron.com/investors (unreachable) | Fail (source unreachable) |
| SHEL | Q3 2026 earnings | 2026-10-29 | No. Shell's advance-notice page and quarterly results page opened but show no date (not on source). A search summary said Oct 29, but I did not see it on an opened page. | https://www.shell.com/news-and-insights/newsroom/news-and-media-releases/2026/advance-notice-of-third-quarter-2026-results-and-third-quarter-2026-interim-dividend-announcement.html | Fail (not on source) |
| BP | Q3 2026 earnings | 2026-10-30 | Not on bp.com (HTTP 403, source unreachable). Oct 30 appears only on energy-pedia, a third-party reprint of bp's trading statement. BRIEF's event text says it is not confirmed on the company page. | https://www.energy-pedia.com/news/general/bp-announces-third-quarter-2026-trading-statement-205649 | Fail (company page unreachable) |
| COP | Q3 2026 earnings call | 2026-11-05 | Yes: company IR page shows Thursday Nov 5, 2026, 12:00 p.m. ET (Sept 24 release). Confirmed, not "expected". Event text is stale. | https://www.conocophillips.com/investor-relations/ | Pass |

## E. Omissions

Did the agent miss something a human analyst would have included? List anything you found
in the ground-truth sources that the brief does not mention (a big headline, an earnings
date inside the window). Each one counts as a Fail in the score below.

- 
- 

## F. Your own test cases

Write two tests of your own that none of the sections above cover. Examples students have
used: "the as-of date on the page matches the changelog date", "no ticker shows a flat
sparkline when the real stock moved", "the page still renders if I delete one ticker's
news list in the data". Write the test, run it, record the result.

| Test | How you checked | Pass / Fail |
|---|---|---|
| | | |
| | | |

## Score

| Section | Passes | Total | Rate |
|---|---|---|---|
| A. Prices | 28 | 30 | 93% |
| B. Weekly change | 4 | 5 | 80% |
| C. News | 4 | 4 | 100% |
| D. Calendar | 3 | 6 | 50% |
| E. Omissions (fails only) | 0 | | |
| F. Your own | | | |
| **Overall** | | | |

Publish only if A and B are 100% and C is at least 80% after fixes. If a row failed, tell
Claude exactly which row and what the correct value is, let it fix only that, rerun the
`qa-reviewer` agent, and regrade that row. Keep the original Fail in this file: a record of
what the agent got wrong is more useful than a clean sheet.
