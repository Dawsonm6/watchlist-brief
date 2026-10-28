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

Refresh date: 2026-10-28    Grader: number-checker agent

## A. Prices (one row per ticker)

Pass if the dashboard's last price is within $0.10 of the ground truth for the same day
and the same price type (close vs intraday). If the agent recorded an intraday price,
compare against the intraday price at about the same time; do not compare it to a close.

Grader note: Google Finance (google.com/finance/quote/TICKER:EXCHANGE) would not open for any
ticker ("Google Finance isn't supported on this device"), so Yahoo Finance history was used,
opened during this run on 2026-10-28 about 11:48 to 11:51 AM EDT.

| Ticker | Date shown | Price type shown | Dashboard price | Ground truth price | Source you used | Pass / Fail |
|---|---|---|---|---|---|---|
| CEG | 2026-10-21 | close | 270.74 | 270.74 | https://finance.yahoo.com/quote/CEG/history/ | Pass |
| CEG | 2026-10-22 | close | 255.21 | 255.21 | https://finance.yahoo.com/quote/CEG/history/ | Pass |
| CEG | 2026-10-23 | close | 253.45 | 253.45 | https://finance.yahoo.com/quote/CEG/history/ | Pass |
| CEG | 2026-10-26 | close | 252.48 | 252.48 | https://finance.yahoo.com/quote/CEG/history/ | Pass |
| CEG | 2026-10-27 | close | 258.98 | 258.98 | https://finance.yahoo.com/quote/CEG/history/ | Pass |
| CEG | 2026-10-28 11:39 AM | intraday | 257.66 | none at 11:39 (Yahoo showed 257.73 at 11:50:09 AM EDT) | https://finance.yahoo.com/quote/CEG/history/ | Fail: intraday, not verifiable at this time |
| CCJ | 2026-10-21 | close | 82.02 | 82.02 | https://finance.yahoo.com/quote/CCJ/history/ | Pass |
| CCJ | 2026-10-22 | close | 78.93 | 78.93 | https://finance.yahoo.com/quote/CCJ/history/ | Pass |
| CCJ | 2026-10-23 | close | 78.60 | 78.60 | https://finance.yahoo.com/quote/CCJ/history/ | Pass |
| CCJ | 2026-10-26 | close | 79.07 | 79.07 | https://finance.yahoo.com/quote/CCJ/history/ | Pass |
| CCJ | 2026-10-27 | close | 82.41 | 82.41 | https://finance.yahoo.com/quote/CCJ/history/ | Pass |
| CCJ | 2026-10-28 11:39 AM | intraday | 82.83 | none at 11:39 (Yahoo showed 82.74 at 11:49:45 AM EDT) | https://finance.yahoo.com/quote/CCJ/history/ | Fail: intraday, not verifiable at this time |
| BWXT | 2026-10-21 | close | 135.11 | 135.11 | https://finance.yahoo.com/quote/BWXT/history/ | Pass |
| BWXT | 2026-10-22 | close | 127.30 | 127.30 | https://finance.yahoo.com/quote/BWXT/history/ | Pass |
| BWXT | 2026-10-23 | close | 127.19 | 127.19 | https://finance.yahoo.com/quote/BWXT/history/ | Pass |
| BWXT | 2026-10-26 | close | 131.20 | 131.20 | https://finance.yahoo.com/quote/BWXT/history/ | Pass |
| BWXT | 2026-10-27 | close | 134.07 | 134.07 | https://finance.yahoo.com/quote/BWXT/history/ | Pass |
| BWXT | 2026-10-28 11:36 AM | intraday | 133.57 | none at 11:36 (Yahoo showed 134.04 at 11:47:35 AM EDT) | https://finance.yahoo.com/quote/BWXT/history/ | Fail: intraday, not verifiable at this time |
| OKLO | 2026-10-21 | close | 27.73 | 27.73 | https://finance.yahoo.com/quote/OKLO/history/ | Pass |
| OKLO | 2026-10-22 | close | 27.01 | 27.01 | https://finance.yahoo.com/quote/OKLO/history/ | Pass |
| OKLO | 2026-10-23 | close | 26.35 | 26.35 | https://finance.yahoo.com/quote/OKLO/history/ | Pass |
| OKLO | 2026-10-26 | close | 25.94 | 25.94 | https://finance.yahoo.com/quote/OKLO/history/ | Pass |
| OKLO | 2026-10-27 | close | 27.33 | 27.33 | https://finance.yahoo.com/quote/OKLO/history/ | Pass |
| OKLO | 2026-10-28 11:39 AM | intraday | 26.59 | none at 11:39 (Yahoo showed 26.55 at 11:50:52 AM EDT) | https://finance.yahoo.com/quote/OKLO/history/ | Fail: intraday, not verifiable at this time |
| SMR | 2026-10-21 | close | 5.50 | 5.50 | https://finance.yahoo.com/quote/SMR/history/ | Pass |
| SMR | 2026-10-22 | close | 5.38 | 5.38 | https://finance.yahoo.com/quote/SMR/history/ | Pass |
| SMR | 2026-10-23 | close | 5.38 | 5.38 | https://finance.yahoo.com/quote/SMR/history/ | Pass |
| SMR | 2026-10-26 | close | 5.27 | 5.27 | https://finance.yahoo.com/quote/SMR/history/ | Pass |
| SMR | 2026-10-27 | close | 5.70 | 5.70 | https://finance.yahoo.com/quote/SMR/history/ | Pass |
| SMR | 2026-10-28 11:37 AM | intraday | 5.60 | none at 11:37 (Yahoo showed 5.60 at 11:49:41 AM EDT) | https://finance.yahoo.com/quote/SMR/history/ | Fail: intraday, not verifiable at this time |

## B. Weekly change (one row per ticker)

The page computes this from the five closes. Pass if it is within 0.3 percentage points of
your own calculation: (last price minus the close five trading days earlier) divided by
that earlier close.

Method: (last price minus Oct 21 close) / Oct 21 close. "Brief" uses the brief's own numbers
(last price = `latest.price`). "Ground truth" uses the Yahoo closes from A and Yahoo's latest
intraday price at the time of checking (about 11:48 to 11:51 AM EDT), since no price at the
brief's timestamp was available. "Changelog" is the percentage typed in the 2026-10-28 entry.

| Ticker | Dashboard weekly change | Your calculation | Pass / Fail |
|---|---|---|---|
| CEG | Brief: (257.66 - 270.74) / 270.74 = -4.83%; Changelog: -4.8% | Ground truth: (257.73 - 270.74) / 270.74 = -4.81% | Pass: all three within 0.03 pp per https://finance.yahoo.com/quote/CEG/history/ |
| CCJ | Brief: (82.83 - 82.02) / 82.02 = +0.99%; Changelog: +1.0% | Ground truth: (82.74 - 82.02) / 82.02 = +0.88% | Pass: max spread 0.12 pp per https://finance.yahoo.com/quote/CCJ/history/ |
| BWXT | Brief: (133.57 - 135.11) / 135.11 = -1.14%; Changelog: -1.1% | Ground truth: (134.04 - 135.11) / 135.11 = -0.79% | Fail: ground truth differs from brief by 0.35 pp (> 0.3). Closes all match; the gap comes from the unverifiable 11:36 intraday price (133.57) vs Yahoo's 134.04 at 11:47 AM, per https://finance.yahoo.com/quote/BWXT/history/ |
| OKLO | Brief: (26.59 - 27.73) / 27.73 = -4.11%; Changelog: -4.1% | Ground truth: (26.55 - 27.73) / 27.73 = -4.26% | Pass: max spread 0.16 pp per https://finance.yahoo.com/quote/OKLO/history/ |
| SMR | Brief: (5.60 - 5.50) / 5.50 = +1.82%; Changelog: +1.8% | Ground truth: (5.60 - 5.50) / 5.50 = +1.82% | Pass: all three agree per https://finance.yahoo.com/quote/SMR/history/ |

## C. News grounding (one row per news item, three per ticker)

Open every link. Pass only if all four are true: the link opens, the headline matches the
article, the article date is within the last seven days, and the "why it matters" line is
supported by the article (not just plausible).

Window: the seven days ending on BRIEF.asOf, inclusive = 2026-10-22 to 2026-10-28.

| Ticker | Headline (first few words) | Link opens | Headline matches | Dated within 7 days | "Why" is supported | Pass / Fail |
|---|---|---|---|---|---|---|
| CEG | AI Power Stocks Fell 7% to 13% in a Week... | Yes | Yes | Yes (Oct 27, 2026, 10:15 PM) | Yes, mostly: "even Constellation Energy (CEG) all fell around 7% from their highs over the last five days" and "Constellation Energy is probably the best positioned to weather an AI pullback, given the long-term contracts it signs." ("Steadiest" is the brief's paraphrase; the article hedges with "probably.") | Pass per https://fool.com/investing/2026/10/27/ai-power-stocks-fell-7-to-13-in-a-week-while-exxon/ |
| CCJ | Cameco (TSX:CCO) After Westinghouse Fuel Plant Start... | Yes | Yes | Yes (Oct 22, 2026) | Yes: "Westinghouse has started building a US$1b commercial LEU+ fuel plant in South Carolina, and Cameco (TSX:CCO), which owns 49% of the venture, now has deeper exposure to next generation nuclear fuel demand." | Pass per https://simplywall.st/stocks/ca/energy/tsx-cco/cameco-shares/news/cameco-tsxcco-after-westinghouse-fuel-plant-start-has-its-va |
| BWXT | BWXT Announces Contract with Antares for TRISO... | Yes | Yes | Yes (Oct 27, 2026, 8:00 AM EDT) | Yes: "multi-year commercial agreement with Antares Nuclear"; fuel "manufactured at BWXT's Lynchburg, Virginia, facility"; "initial allocation of 1 MTU ... with the ability to increase"; no contract value disclosed. | Pass per https://stocktitan.net/news/BWXT/bwxt-announces-contract-with-antares-for-triso-nuclear-fuel-2pv6kngoypof.html |
| OKLO | Energy Fuels Jumps 9% on $126M Australian Financing... | Yes | Yes | Yes (Oct 27, 2026, 12:02 PM ET) | Yes: "Part of the move is shared across the nuclear group, with NuScale Power and Oklo both climbing alongside the uranium fund." No Oklo-specific news cited. | Pass per https://247wallst.com/investing/2026/10/27/energy-fuels-jumps-9-on-126m-australian-financing-for-rare-earth-project-nuscale-power-climbs-7-oklo-gains-6/ |
| OKLO | Oklo Is Now Down 63% This Year... | Yes | Yes | Yes (Oct 26, 2026, 2:42 PM ET) | Yes: "TD Cowen started coverage of Oklo stock with a Hold rating and a $26 price target"; "Oklo still has no commercial power sales"; "keep OKLO stock positions small given the cash burn and dilution risk"; "Licensing is the next hurdle." | Pass per https://247wallst.com/investing/2026/10/26/oklo-is-now-down-63-this-year-is-oklo-stock-dead-money-or-due-for-a-bounce |
| OKLO | Nuclear Energy Analyst Roundup: Wall Street Weighs In... | Yes | Yes | No (Oct 21, 2026, 9:59 PM EDT; window starts Oct 22) | Yes: Citi cut its Oklo target from $57.50 to $33, kept Neutral. | Fail: article dated Oct 21, outside the Oct 22 to 28 window, per https://finance.yahoo.com/energy/articles/nuclear-energy-analyst-roundup-wall-015948632.html |
| SMR | Energy Fuels Jumps 9% on $126M Australian Financing... | Yes | Yes | Yes (Oct 27, 2026, 12:02 PM ET) | Yes: same sentence as above; NuScale "up 7% to $5.64 ... as reactor developers join the advance." | Pass per https://247wallst.com/investing/2026/10/27/energy-fuels-jumps-9-on-126m-australian-financing-for-rare-earth-project-nuscale-power-climbs-7-oklo-gains-6/ |
| SMR | Nuclear Energy Analyst Roundup: Wall Street Weighs In... | Yes | Yes | No (Oct 21, 2026, 9:59 PM EDT; window starts Oct 22) | Yes: Citi cut its NuScale target from $6.50 to $4, kept Sell, implying downside of more than 27%. | Fail: article dated Oct 21, outside the Oct 22 to 28 window, per https://finance.yahoo.com/energy/articles/nuclear-energy-analyst-roundup-wall-015948632.html |

(Add rows as needed. Fifteen items is normal for five tickers.)

## D. Calendar (one row per event)

Pass if the event and its date appear on the source linked, and the date is in the future
relative to the refresh date.

| Ticker | Event | Date shown | Confirmed on source | Pass / Fail |
|---|---|---|---|---|
| CEG (market-wide) | FOMC rate decision, Oct 27 to 28 meeting | 2026-10-28 | Yes: Fed calendar lists October 27-28, 2026 (decision day = asOf, not before it) | Pass per https://www.federalreserve.gov/monetarypolicy/fomccalendars.htm |
| CEG | Q3 2026 earnings, before the open (marked expected) | 2026-11-09 | No: Constellation IR events page returned 403; no Constellation press release or 8-K for the Q3 date found. Only Earnings Whispers (Nov 9), TipRanks (est. Nov 9), AJ Bell (Nov 6), which do not count. Brief does label it "expected". | Fail: not confirmed by the company; IR page https://investors.constellationenergy.com/events-and-presentations returned 403 |
| CCJ | Q3 2026 results before the open; call 8:00 a.m. ET | 2026-10-30 | Yes: Cameco release says Q3 results Friday, October 30, 2026, before markets open, call at 8:00 a.m. Eastern | Pass per https://www.cameco.com/media/news/cameco-provides-date-for-2026-q3-results-conference-call-and-webcast |
| BWXT | Q3 2026 results after the close; call 5:00 p.m. ET | 2026-11-02 | Yes: BWXT's own Business Wire release (Oct 1, 2026), reprinted on Finviz: results Monday, November 2, after market close, call 5:00 p.m. ET. BWXT IR page returned 403. | Pass per https://finviz.com/news/398036/bwx-technologies-to-announce-third-quarter-2026-results-on-monday-november-2 (Business Wire reprint) |
| OKLO | Q3 2026 earnings, before the open (marked expected) | 2026-11-06 | No: Oklo IR events page lists no upcoming events; no Oklo "Announces Date for Third Quarter 2026" release found on Business Wire. Only Earnings Whispers and one unrelated-looking site give Nov 6. Brief does label it "expected". | Fail: not confirmed by the company per https://investor.oklo.com/events-and-presentations/default.aspx |
| SMR | Q3 2026 earnings conference call, 5:00 p.m. ET | 2026-11-05 | Yes: NuScale's own Business Wire release (Oct 6, 2026), republished by Investing News: call Thursday, November 5, 2026, 5:00 p.m. ET. NuScale IR events page returned 404. | Pass per https://investingnews.com/nuscale-power-to-hold-third-quarter-2026-earnings-conference-call/ (Business Wire reprint) |

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
| A. Prices | 25 | 30 | 83% |
| B. Weekly change | 4 | 5 | 80% |
| C. News | 6 | 8 | 75% |
| D. Calendar | 4 | 6 | 67% |
| E. Omissions (fails only) | 0 | | |
| F. Your own | | | |
| **Overall** | | | |

Publish only if A and B are 100% and C is at least 80% after fixes. If a row failed, tell
Claude exactly which row and what the correct value is, let it fix only that, rerun the
`qa-reviewer` agent, and regrade that row. Keep the original Fail in this file: a record of
what the agent got wrong is more useful than a clean sheet.
