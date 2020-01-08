
# EDF Questionnaire

## Questions

1. What, professionally, are you proudest about in the last year?
2. Name one inefficiency or missed profit opportunity that you would pursue if you had full control at your current organization?
3. What is one word that your boss would use to describe you?
4. If you had the EDF job at the salary you asked for, what type of an opportunity would you then LEAVE this job for?
5. Tell me how you would go about constructing an FTR trading portfolio. Make any assumptions about capital, risk constraints, etc. that you need to, but clearly outline what those assumptions are?
6. If you were to buy a path in an FTR auction, how would you determine the right bid price and bid curve?
7. What do most people trying to model congestion in ISO markets get wrong?
8. Pick 5 out of the following qualities which you believe best describe you. Rank those 5 in the order of most descriptive to least. (commercial, opportunistic, thoughtful, diligent, team player, enthusiastic, satisfied, curious, obsessive, aggressive, winner, creative, charismatic, careful, confident)

## Responses

1. In general, I'm proud of the way that I was able to quickly and effectively take on several different responsibilities in the Grid Analysis group at ERCOT (after moving from the CRR group in Dec. 2018, which had vastly different responsibilities).

- I became the "primary" in conducting Voltage Profile Seasonal Studies despite never seeing how these twice-a-year studies were conducted before.
- I did nearly all of the programming for computationally intensive contingency analysis tool that can take real-time EMS cases, run N-2 analysis (relatively) quickly, and generate interpretable results for managers.
- During the "tight" summer, I developed displays to enhance monitoring of real-time system conditions.

In all, I feel like I've developed a better understanding of the balance of markets (which I got some of from my CRR role) and reliability in grid operations.

2. Arbitrage across CRR auctions for the same TOU-month, i.e. selling a CRR for a profit (instead of simply holding it and allowing it to settle in DAM) after buying it in an earlier auction.

I'm not sure I would really call this an inefficiency since it's a known strategy (and I believe DC Energy is relatively known for doing this). It can certainly "backfire", e.g. if the sold CRR would have ended up making a larger profit (compared to what you sold it at). Nonetheless, I think it can be a sound play for CRRs sourcing/sinking at nodes where prospects have changed since the time that it was purchased. For example, if you purchased a CRR across a path where a transmission project is suddenly expected to be completed a couple of months in advance, thereby negating the congestion that you had expected to occur in the area, then it would be worthwhile to try to sell the CRR (either for a profit, or possibly for a small loss, if it is deemed to be better than the loss than might be expected if it is held) before it is settled in the DAM. The same might be said for a new RAS that is implemented (unexpectedly) that circumvents re-occurring congestion in an area that had, before then, been a target for hedging price differences.

Aside from this, there is a difference in how phase-shifting transformers are treated in the ERCOT CRR and DAM software that could possibly be exploited, but I'm not really sure to what extent. (Of course, there are always going to be differences in the CRR and DAM models, but this is a "fundamental" difference.)

3. Probably "diligent", closely followed by "disciplined".

For as long as I can remember, my teachers, peers, and family have applauded my work ethic and discipline. When I have my mind set on achieving something, I create a course of action for myself (typically, not something  "too" strict, i.e. having dates, but, instead, guided by specific tasks to be completed) and hold myself accountable towards fulfilling what I've outlined for myself. My diligence, combined with discipline, has been key for me when preparing for multiple exams in a short span of days (and doing well on them); preparing for solos/concerts (when I played music when I was younger); exercising consistently, etc. These traits have undoubtedly transferred to my everyday work.

4. Assuming EDF's work culture is satisfactory (along with the salary), there are two reasons why I would consider leaving: (1) location and (2) career change.

1) I've lived in either San Antonio or Austin my entire life, and I really enjoy both cities. (I also had an internship in Houston. The city wasn't as appealing to me at the time, but I think I can grow to like it more.) I like living close to my parents and my younger brother, so I would prefer to stay in one of these cities.

2) I've always been fascinated with the field of sports analytics, so some kind of opportunity in that industry would be enticing. This is not to say that I would certainly leave for that kind of opportunity. (I've had a sports analytics job offer in the past and turned it down.) From my understanding, there is lots of turnover (and worse job stability) in that field compared to energy/electricity markets, as well as lower pay and longer hours, all of which makes it somewhat less attractive. 

5. As mentioned, there are a myriad of assumptions that need to be made in preparation for developing a strategy for FTRs. For the sake of argument, let's say that
  
    1) I'm purely a financial trader, i.e. that I don't own any generation or load assets;
    2) I don't have stakes in another commodity market, e.g. gas or oil (that might oblige me to hedge certain settlement points);
    3) I'm only focused on the ERCOT region.
    4) I can afford to buy 10 to 50 paths in a given auction (at a reasonable price and quantity); 
    5) I'm risk neutral (not risk averse or risk acceptant), i.e. that I'm indifferent to a 50/50 lottery and a guarantee for a certain amount of money, and that I want to maximize my expected returns.

(Surely there are more assumptions about capital, risk, and obligations that I'm missing.)

Now, regarding price and congestion forecasting, I would use an approach that leverages simulation and sensitivity analysis (and, given the appropriate time and computational resources, even AI) to model (specifcally, to model the DAM, but also CRR relevant information, such as bids from other participants). This would involve building out a large set of scenarios that accounts for the variability in the many "inputs" to such forecasting (and, of course, using software to run the simulations):

- transmission topology;
- weather conditions (in particular, the most extreme temperatures/worst-case conditions);
- hourly nodal demand---which, among other things, is a combination of weather-dependent residential load, price responsive load, and more constant industrial load);
- fuel prices (particularly, that of natural gas), which plays a role in unit availability;
- (hourly) generation characteristics, i.e. intermittency of renewables, startup and operating costs, heat rate curves, ramping capabilities, max and min capabilities, AS capabilities, etc.;
- generation outages---which tend to have a seasonal pattern;
- transmission outages---which, aside from maintenance needs, may be related to new equipment energization;
- DC tie scheduling (the means of importing/exporting in ERCOT);
- contingencies and RASs;
- equipment ratings;
- bidding behavior of other market participants.
    
Some of these things are certainly more "uncertain" than others (bidding behavior and forced generation outages) and might potentially be treated as a "constant" (a constant "unknown") in simulations. Those inputs that are more "unknown" than "uncertain" are probably better evaluated with re-enforcement learning techniques (which is beyond the scope of simulations and sensitivity analysis but would be a worthwhile venture given sufficient time and resources).

I should note that each power flow simulations would calculate/incorporate generation shift factors, which are instrumental to relating constraints to LMPs. The likelihood of constraints themselves is implicitly dependent on inputs such as topology, equipment ratings, nodal demand, etc.

From the simulation output, I would identify locations where congestion is most likely to occur and, along with it, where extreme prices are most likely to occur. I would compare this to historical prices---partially assuming that other market participants will behave as they have before and/or that they will use historical prices in their own forecasting analysis---and identify the largest discrepancies, particularly those that would result in the best chances of profit. Really, if this kind of economic maximization can be built into the simulations---perhaps as the objective of some kind of optimization procedure that is fed the simulation output---that would be best. But, even with this optimization, I would need to be careful with how I'm defining this economic goal. How do I balance (1) "maximum" profit across any single simulation (perhaps with a very low probability) versus (2) "average" profit (accounting for a range of probabilities)? My thought would be to create a mixed portfolio---make offers on a couple of the high-risk/high-reward source-sink pairs (despite my risk-neutral mentality) at prices lower than what I think they could garner, but focus on offers on the pairs that I've projected to be profitable across a larger proportion of simulations (at lower margins).

With all of this being said, I do not mean to undermine the viability of a more "fundamental" approach that focuses on only a handful of "simplified" models with specific economic/operations assumptions. This can be a reasonable approach if one does not have the computational resources or expertise to employ a stochastic approach like the one I've described.

6. First, I would use the simulation-based approach described above to give me a range of probabilities for the price of a given node in each hour.
    
Next, if I haven't also used this approach to "directly" give me the source-sink pairs with the largest price discrepancies (averaged across all hours in a TOU-month), I would do this next.
    
Then, if I think that other market participants are unlikely to see the same opportunity as me, I would assume that they follow their typical bid patterns, and make a bid curve offer that is highly likely---to put a number on it, let's say three standard deviations above the average for that path, according to historical data---to be awarded at the highest point of the curve. The lowest point of the curve might be two standard deviations below the historical average. The other price points would build out a concave upwards curve between these maximum and minimum points of the bid curve. (This scenario is for a buy bid.) On the other hand, if I do think that other market participants are likely to see the same opportunity, then I would employ a similar strategy, adding some reasonable "buffer" to the historical averages.
    
If possible, I would use/design software to make recommendations for me regarding bid curves (given my tolerance for risk and profit goals as inputs). Ultimately, I would still want to have room for manual intervention regarding the final submitted curve for a given path.

7. Well, I'm not sure people are completely wrong about certain aspects with their approaches. If I had to pinpoint one thing, I think I would say that there might be an over-reliance on historical data regarding constraints, LMPs, and clearing prices. (Apologies if this is not in the scope of what you mean by "modeling".) Of course, historical data can be useful, but I really think it should be used primarily for "validation purposes". One is best off modeling the system (as described before) and using the historical data to "check" that your simulation output/findings are reasonable. 

Aside from this, I think that, in general, it's difficult to quantify the amount of uncertainty associated with all the "variables" that play a role in price and congestion forecasting. Even if one has a pretty good gauge on which factors are more uncertain than others, one should be ready to "update" these notions as time passes and things change.

8. Qualities:

    1) diligent
    2) careful
    3) team player
    4) thoughtful
    5) curious


# Christine Hynes Assistance

## "Interview Prep" Email on 1/7/2020

"I put this together for a different client search. At that time, my client was hiring a power engineer who was “green” to working on a trade floor. I worked with my client to put together this summary. 

My client was looking to hire someone that wanted to work on a commercial trade floor where you need to be able to “get to the point” and “figure out what is important” to help them make decisions around trading / generating revenue. A few things that I think clients evaluate in general are below. For the Adaptability/Flexibility comment that was specific to the job they were interviewing for. The role at EDF is focused on EDF so one market but in general, it is important to be Adaptable and Flexible.

+ Technical Modeling Skills: Translating your resume/extent of modeling experience and how it relates to their job; will assess how you build your models, use data, and analyze data/outputs;

+ Cultural Fit: Looking for someone who is comfortable working in a fast-paced trading environment. Sometimes you need to give your opinion with 80% of the information or you will have 2 weeks to do the model rather than 4-6 weeks;

+ Adaptability/Flexibility: They expect this new hire to be efficient to cover multiple ISOs. Starting out the focus of this role is more on breadth than depth of knowledge in any one ISO;

+ Communication Skills:  This is a hard one to describe but basically covers the 4 items above and how you communicate during the interview. It can be explaining complex theories and models in a less complicated way to a non-engineer;

+ Commercial Sense: Knowing what matters and when it matters and, focusing on anything that drives results. They are seeking revenue/profits and not focusing on things that don’t matter as much to the end goal of making revenue/profits now and making revenue/profits over time (examples include modeling improvements that help make revenue/profits in the future are a good sort of thing OR there could be some nuance to your modeling that their competitors have not capitalized on in the FTR markets). Commercial sense is translating knowledge into revenue/profits efficiently;

+ Goals: Looking for someone that is smart, motivated and has the personality to work in a team environment."

## Notes from Phone Conversation with on 1/7/2020

+ Always discuss the "why".

+ Possibly be prepared to:
    + Discuss a story about when I had to convince management of something
    + Why path a instead of path b?

+ What questions should I ask the interviewers?
    + What would the expectations for me be (first 3 months vs 3 - 9 months vs. 1 year from now)? How will success be quantified?
    + What is a typical day like?
    + How much interacting with customers will there be? What are the challenges with working with customers?
    
# ["Use FTR ARR to Hedge Financial Risk and Enhance Power Market Models"](https://www.youtube.com/watch?v=kj1zy2RWgok) YouTube Video (Uploaded 2/20/2017)

## Basic knowledge of ARR and FTR

### Concept

#### ARR (Auction Revenue Rights)

+ Tenor: Annual allocation
+ Procure: Free but have to be nominated
+ Source: ISO hosted annual FTR auction
+ Risk: Revenue or charge Based on annual FTR

#### FTR (Financial Transmission Rights)

+ Tenor: One month to three years out
+ Procure: Participating in FTR auctions
+ Source: DA LMP congestion components
+ Risk: Revenue or charges settled in DAM. (LMP congestion components delta between source and sink.)

#### Cash Flow

+ DA -> FTR -> ARR
+ Profits
  + ARR: Load and transmission service
  + FTR: mostly generators and financial institutes
  + DA/RT deviation: mostly financial institutes

### Mechanism - ARR

#### Physical

+ A collection of source and sink pairs
  + **Source: Generators (Stage 1 and 2), HUBs and ZONEs (Stage 2)**
  + Sink: ZONEs
+ Simultaneous Feasibility Test (SFT)
  + Ensure available transmission capability **covers ARR nominations**
  + Source as generator and sink as load
  + N-0 and N-1 conditions enforced
  + Network model with approved upgrades and outages
  + **If not feasible then prorate request by MW nominated**
+ **Regional Transmission Expansion Plan (RTEP)**
  + **SFT covers 10 year load growth**

#### Financial

+ Entitlement and obligation (benefit or liability)
+ Based on LMPs from annual **FTR auction**
+ **Allocated in an annual (March) two-stage process**
  + **Stage 1**
    + **Stage 1A: historical resource to base load**
    + **Stage 1b: historical resource to peak load**
  + **Stage 2: 3 rounds allowing any sources to the native load zone**
+ Can be converted to FTR and settled in DA
+ Can be reconfigured by acquiring alternative FTRs or OTC product

### Mechanism - FTR

#### Physical

+ A collection of source and sink pairs
  + **Source/sink: ZONEs, HUBs, Interface, Gen, and Load**
+ Simultaneous Feasibility Test (SFT)
  + **Objective: Maximize quote based bid value of a set oof SFT-satisfied FTRs**
  + Ensure available transmission capability **considers all existing FTRs and new FTR bid/offers**
  + Source as generator and sink as load
  + N-0 and N-1 conditions enforced
  + Network model with approved upgrades and outages
  + **Highest bid-based valued combination of SFT feasible FTR are awarded**

#### Financial

+ Entitlement and obligation (benefit or liability)
+ Based on LMPs from **DAM**
+ Allocated in FTR auctions
  + Long-term: 3 rounds, assuming ARRs from current year convert to FTR
  + Annual: 4 round, 25% capacity each, entire system
  + Monthly: 1 round, current planning year
+ Can be converted to FTR and settled in DA
+ Can be reconfigured by acquiring alternative FTRs or OTC product
+ **Credit requirement**
  + **Sum of all FTR bids**
  + **Undiversified extra**
  + **Deduct ARR revenue**

[^1]: This is confusing to me.

## Value of ARR and FTR

### Market capacity - ARR

PJM ARR revenue by load zones ($MM) table

+ Big picture
  + Contango trend since PY1314
  + Hint of reversal trend starting PY1617
+ Zonal observations
  + Large volatilities, e.g. AEP, BGE, COMED, PECO
  + Fundamental drivers
    + Commodity prices
    + Transmission outages and upgrades
    + Generation retirement
    + Environmental rules
  + Challenges
    + Competitive load serving pricing
    + Dynamic ARR nominations
    + Intermediate hedging

### Market capacity - FTR

Annual FTR investment and return for ISOs (data from ABB Energy Velocity Suite) graph shows:

| Year        | 2013        | 2013        | 2013        | 2014        | 2014        | 2014        | 2015        | 2015        | 2015        | 2016        | 2016        | 2016        |
|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|
| ISO         | Auction $MM | Settled $MM |  Profit $MM | Auction $MM | Settled $MM |  Profit $MM | Auction $MM | Settled $MM |  Profit $MM | Auction $MM | Settled $MM |  Profit $MM |
| ERCOT       | 177         | 236         | 60          | 309         | 357         | 48          | 675         | 130         | -545        | 367         | 201         | -166        |
| Grand Total | 1847        | 5450        | 3603        | 3568        | 4461        | 893         | 3394        | 3146        | -248        | 2671        | 2938        | 267         |

+ Polar vortex in PY13-14 produced much igher than expected FTR revenue
+ Risk following FTR investment in 2014 and 2015 produced lower than expected return
+ Mild weather in PY15-16 caused losses in FTR/
+ Starting from PY1516 and PY1617, risk/reward balancing and starting a contango trend

Same graph, but for Major IPPs and LSEs only
(numbers are much smaller, but follow the same overall trend)

+ Active FTR Hedging activities by utilities in PJM, MISO, NYISO, ERCOT
+ Potential growth in CAISO, SPP
+ Increasing hedging cost
+ Risk following behavior

## ARR and FTR Strategy

### Importance

#### Pnode->ZONE->HUB

+ IPP position:
  + Are short HUBs
  + Are long with generator Pnodes
+ LSE
  + Are short ZONEs

+ Only HUB is fully tradable with good liquidity
+ ZONE/HUB spread trades once a month in FTR or once/several days in OTC market
+ Gen. Pnode-ZONE trade only once a month in FTR (auction is competititve)

***Verbal comments:***
+ Generator Pnodes are cheapest.
+ ZONEs are most expensive due to load forecast and dispatch "issues".
+ Link betwee the 3 types is very dynamic.
  + e.g. ZONE price might be high (and changed since last month), but HUB price doesn't change.
+ IPPs are short HUBs due to hedging their generation
+ LSEs hedge by buying HUBs

### Advantages

#### OTC Hedging [^1]

+ Hedge target
  + Basis and spread
+ Liquidity
  + Wide bid/ask
  + Low frequency
+ Risk control
  + Single directional bet
  + High exit cost
+ Analytical
  + Zonal or stack model

[^1]: RTO/ISOs don't have visibility to this.

#### FTR/ARR Hedging

+ Hedge Target
  + Basis and Spread
  + Hedge to congestions
    + Driver
    + Characteristics
+ Liquidity
  _ Guaranteed monthly liquidity
  + 1-3 year outlook
+ Transparency
  + ISO host
+ Risk Control
  + Bid layers
  + Leverage
+ Analytical
  + Nodal forecast tools, e.g. PROMOD

***Verbal notes:***

+ PROMOD includes complex cost-production models

***Personal interpretation:***

+ FTR modeling is more complex, but there is more opportunity (for diversifying portfolio)
+

### Modeling and Application - MOdeling Techniques

####  PROMOD ARR model [^1]

[^1]: ARRs are PCRRs in ERCOT

+ Base Case (using reference case for next planning year)
  + Transmission outages
  + Fuel forecast
  + Major RTEP upgrades
    
+ ARR Valuation (using ARR base case)
  + Stage 1
    + Optimal ARR revenue
    + PROMOD forecast
    + Historical value
  + Stage 2
    + Identify missing constraints
    + Shift factor analysis
    + Propose additional ARR

#### PROMOD FTR model

+ Base Case (using ARR base case)
  + All scheduled outages longer than 3 days [^1]
  + Fuel forecast
  + RTEP upgrades with timelines
  + **Perturbations** [^2]
    
+ ARR Valuation (using FTR base case)
  + Zonal Basic Forecast
    + Compare with OTC market hedge in OTC or FTR. OTC=FTR?
  + Competition Forecast
    + Identify congestion with impact on basis or spread
    + Propose FTR candidates

[^1]: This is 5 days in ERCOT.

[^2]: i.e. sensitivity analysis.


# "Fixed Hedging" Finding

+ DC Energy, SESCO, and NRG have most prominently employed the buy-then-sell strategy with success (including both obligaions and options, from Jan. 2013 to Oct. 2018). Saracen was also pretty profitable with this strategy if only considering obligations.
+ CPS and Brazos employed the sell-then-buy strategy to some success. (Luminant was not so successful with it.)
+ HB-to-HB resulted in the most negative (i.e. "best") relative transaction cost (net transaction cost minus total transaction cost) with buy-then-sell strategies. RN-to-RN resulted in the most positive (i.e. "worst") relative transaction cost. (HB-to-LZ had the most total transaction cost.) 
+ RN-to-HB resulted in the most negative (i.e. "best") relative transaction cost (net transaction cost minus total transaction cost) with sell-then-buy strategies. (HB-to-HB was very close.) RN-to-LZ resulted in the most positive (i.e. "worst") relative transaction cost. (HB-to-LZ had the most total transaction cost.)
+ LTAS.SEQ4-to-LTAS.SEQ1 resulted in the most negative (i.e. "best") relative transaction cost with buy-then-sell. LTAS.SEQ1-to-MONTHLY resulted in the most positive (i.e. "worst").
    + Intutitively, this makes sense. "Smart" bidders would buy early and sell later. "Desperate" bidders would buy late to manage risk, even at a negative rate.
+ LTAS.SEQ1-to-MONTHLY was the only negative relative transaction cost with sell-then-buy.
    + Intuitively, this checks out. Those who sold before the last opportunity might make offers at lower rates in the final auction, simply to guarantee a small fixed profit.
    + It may be a bit suprising not to see any other auction-to-auction combinations (e.g. LTAS.SEQ2-to-MONTHLY) without a negative relative cost.

# Penny Bids

+ Between Jan. 2015 and Dec. 2019 (only Dec. 2018 for Monthlys), the % of all bids that were "penny bids" (i.e. a bid with a price of $0.1 MW for any MW value) ranged from between 40% and 60% most of the time. There was no discernable difference based on the type of auction. The number seemed to gradaully decrease since the beginning of 2017 for all auctions aside from Seq. 4.
+ The % of all bids that were are awarded penny bids range from 8% to 14%, irregardless of auction type.
+ MWh, absolute value of transaction amount, and absolute value of transaction amount per awarded MWh were all a bit higher for LTAS compared to Monthlys, although the difference was not super drastic.
+ % of all bids that are penny bids has steadily increased, while % of bids that are awarded penny bids has steadily decreased.
    + Intuitively, this makes sense.
    
# Price Convergence

+ Compared HB_WEST-to-LZ_WEST PTP prices for all three markets (in regards to a concern about high prices in the DAM and RTM) from Nov. 2017 through Jul. 2018 and found that they followed the same trends (given that the CRR month as lagged by 2 months since CRR bids are submitted ~45-60 days in advance of the month that is targeted). The same was true for the other three HB-to-LZ paths (with one exception for CRR in the South in 1 month).

# CRR Settlement Point Prices (with Maps)


"WARNING: LONG EMAIL

All,

I’ve done some work in evaluating the strength of the relationships among settlement point prices (SPPs) across the three ERCOT markets—CRR, DAM, and RTM—both quantitatively and visually, using the SpaceViz tool—an offline version of the ERCOT contour map application. In all, I found that the prices in the three markets do converge relatively well, which is a positive indication of market health (by my interpretation). Additionally, when analyzing the CRR market specifically, I found that the trends in prices reflect behavior that we have seen in recent CRR auction results, such as higher bid prices overall, higher clearing prices in the Far West, and abnormal CRR congestion (leading to high prices) in the North zone (particularly in July), among other things.

## METHODOLOGY

Maybe the first question that comes to mind is “Where did you come up with CRR SPPs?”. Well, in an endeavor to “derive” them from point-to-point CRR clearing prices, I found that SP “shadow prices” are posted for each CRR auction on ERCOT’s website. (How did I not know about this before?). Specifically, for the following analyses, I used the values from CRR Monthly auction result postings at http://www.ercot.com/mktinfo/crr (in the “Common_SourceAndSinkShadowPrices.csv” file.)

A couple of notes about this CRR data:
    + To my knowledge, this data is not found “directly” in any of the CRR databases. (Nonetheless, it is theoretically possible to calculate them from various raw data, as I was attempting to do beforehand.) Rather, these prices are calculated by a database procedure that is executed only when the auction results are posted.
    + Most values for a given auction generally range from -15 to 15, with STP_STP_G1 and STP_STP_G2 always having a value of 0. It is evident these resource nodes (RNs) are used as “reference” points from which all other SPPs are derived (using point-to-point CRR clearing prices). (This is actually how I was attempting to calculate CRR SPPs beforehand.)

To give an example of how these values correspond to point-to-point CRR clearing prices, consider the following actual example. The CRR clearing price for a BUY OBL bid for the August 2018 Monthly for a specific time period for the path sourcing at HB_HOUSTON and sinking at HB_NORTH is -$0.24. 

The CRR clearing price (under the same conditions) for the path sourcing at HB_HOUSTON and sinking at STP_STP_G1 (with a reference value of $0) is $2.93. 

The value for HB_HOUSTON should be ~$2.93, and the value for HB_NORTH should be $2.69 (i.e. (-$0.24 - x) – ($0 - $2.93) = $0 - x = $2.69). This is found to be true.

    + Only data for the past 12 Monthly auctions are posted. (Ideally, more data would be nice, but this is still a relatively good sample size.)

Next, a couple of notes about how the data for all three markets was compiled and treated on an “equal” basis:
    + Only SPs appearing in CRR auctions and which have location information for the SpaceViz application are considered.
        + The CRR-inclusive criteria means that that combined cycle turbine (CCT) RNs (of which there are about 70) are removed from consideration.
        + The location criteria means that the SPs for DC ties, Hubs (HBs), and Load Zones (LZs) are disregarded.
    + HBs and LZs obviously cannot be represented explicitly on the maps. Nonetheless, the HB and LZ SPPs seem to generally be reflected by the prices of SPs within each zone.
    + Regarding the DC ties, it is not completely clear why there is not location information for these. Anyways, the values for these SPs are relatively volatile and may be more likely to distort numerical/visual analysis than to enhance it.
        + In applying the above criteria, the result is that 554 SPs are considered across the three markets for all months.
    + Prices for DAM and RTM are pulled from ISM databases (MMS_MIDB.DAM_SPP_OT and MMS_MIDB.SCED_STLPNT_LMP_OT). The average of each SP for a given CRR time-of-use (TOU) block is used.
        + For those unfamiliar with the CRR TOUs, there are 3 TOUs: 
    + Off-peak (OP), hours ending 1 through 6 and 23 and 24 for all days of the week;
    + Peak Weekday (PWD), hours ending 7 through 22 for business days; and 
    + Peek Weekend (PWE), hours ending 7 through 22 for Saturday, Sunday, and holidays.
        + TOU is the most “granular” temporal basis that CRR has.

## ANALYSIS

### Market-to-Market SPP Correlations

The following heat map illustrates the month-specific, TOU-specific correlations of SPPs across each of the three possible combinations of markets.

A couple of things to note before looking at the results:
    + Correlations here are calculated for ranks of SPPs relative to a given market and TOU.
        + For example, given that there are 554 SPs in the CRR market for the December 2018 Monthly Auction and the Off-peak TOU, the SP with the highest price for this month and TOU is assigned a value of 554, the SP with the next highest value is assigned a value of 553, etc., and the SP with the lowest value is assigned a value of 1.
        + This methodology is helpful for accounting for the vastly different “raw” price ranges across each market. On the other hand, this approach has the disadvantage of exaggerating the differences in SPs with nearly identical prices (and, conversely, suppressing the differences in SPs with vastly different prices where there are no other prices in between).
    + Correlation values can range from -1 to 1, where 1 indicates a perfect positive relationship (in this case, meaning that all SP ranks are identical), 0 indicating no relationship, and -1 indicating a perfect negative relationship.
        + The graph caps the minimum value at 0 because only a handful of values were negative, so a full color scale ranging across from -1 to 1 would not illustrate some of the “minute” differences as well.

A couple of takeaways from this visual:
    + We should expect to see that RTM and DAM correlations (the bottom grid) to be higher than those involving the CRR market (the top and middle grids), which is evident. However, perhaps it is a bit surprising to see that CRR corresponds nearly as closely with DAM as does RTM (in the top grid),  and that the values for the correspondence between CRR and RTM are (mostly) positive and strong as well (although they are still the “weakest” of the 3 possible market combinations).
    + The data for the last month shown—the current month of August 2018—probably should not be considered heavily since the RTM and DAM data for this month is incomplete. (Data was retrieved on 8/9/2018 for these markets.)
    + There are relatively weak correlations in a couple of months/TOUs. Some further investigation could be done to identify specific reasons for the low correlations for these time periods.
        + Across all 3 market combinations and each TOU for July 2018. 
        + The PWD correlations with RTM (bottom two grids) in December 2017 and February 2018.
The SPP Since Nodal Go Live webpage (at http://trend.ercot.com/Summaries/SPPSinceNodalGoLive) offers a good starting point for conducting further investigation. For example, to try to explain the PWD discrepancies in December 2017, it seems like the 7th day of the month may have had a strong effect. It’s not necessarily that the HB prices are of different magnitudes on this day between DAM and RTM (which is not an extremely uncommon occurrence), but that the prices in RTM are not clustered closely to one another, resulting in geo-spatial discrepancies in prices.


We can visualize these numbers using the SpaceViz application. For example, the following triplet of maps provides an example of a month-TOU combination with strong, positive correlations across all three markets. In this case, the Peek Weekday TOU for September 2017 is shown.

Next, here is an example of a “mediocre” fit—June 2018’s Peak Weekday TOU block. The CRR contour is noticeably different from the other two in the south.

Finally, July 2018’s Peak Weekday maps provide an example of “poor” price convergence (mostly between DAM and RTM and CRR and RTM). High prices in the RTM are spread “widely” throughout the west and central Texas. However, there is not nearly as many high prices in central Texas in DAM and CRR. Additionally, high prices in DAM and RTM in the north-Dallas area are not as apparent in the CRR contour.

A couple of notes about these maps:
    + For those interested in seeing the maps for all months and TOUs, I’ve placed them in my folder on the Market Operations Support drive (\\ercot.com\business\Market Operation Support\aelhabr\SpaceViz-output). There are versions with the three maps combined (as shown above), as well as individual PNG files for singular market-month-TOU combinations. (Hopefully the naming convention of the folders/files is self-explanatory.)
        + The SpaceViz tool does not directly combine maps in triplets as is seen in the images shown above. I did this with some code.
    + For the purpose of understanding trends over time (mostly for CRR, where TOU and month is the most “granular” unit of time), I have found that it is very useful to navigate through these in temporal order with a PNG viewer application (like Windows Photo Viewer). Specifically, comparing OP to PWD is instructive. The difference in prices for wind/solar-affiliated RNs in the Far West (and Panhandle) between off-peak on on-peak hours is apparent. CRR prices tend to be higher for a given month in the OP TOU block relative to the PWD and PWE blocks, which reflects the congestion that we have seen in the past handful of months at Off-Peak hours in these areas.

###  CRR Prices

As a a member of the CRR team, I wanted to dive deeper into the numbers for CRR market.

To begin, I looked at the HB and LZ CRR SPPs, which provide a general “gauge” for the market. Here (and for the subsequent analysis), I’ve left the CRR price values in their original form (since I’m not comparing prices across multiple markets).


Observations:
    + The South, North, and West LZ SPs (yellow, maroon, and orange) stand out.
        + The LZ_SOUTH price is interesting because it is consistently the highest.
        + The LZ_NORTH price is noticeably high in July 2018 for the two on-peak TOUs in the past 2 months. This reflects the abnormally high CRR congestion seen in the North for these 2 months.
        + The LZ_WEST price is interesting due to the increase in its value relative to all other SPs.
        + The high values in August 2018 for LZ_WEST seem to be a consequence of high prices for HOVEY_GEN and LASSO_GEN RNs (in the WEST zone) for this month, which have the two highest price values for this month compared to all other points in all other months.

Keeping this last point about specific RNs in mind, let’s break down the zonal prices by HB, LZ, and RN in each zone. With this plot and all subsequent ones, prices for a given month are weighted by the relative number of hours for the TOU for the month.

Takeaways:
    + As we should expect, the LZ prices are generally higher than the HB and RN prices, the RN prices generally fall in between those for the LZ and HB for a given zone.
    + The “profile” of the three lines for each zone are very similar (in this plot and others). This is to be expected—since the CRR prices are “relative” to one another—and is a good check on the validity of the underlying data.

Now, let’s break down the CRR SPP data in the following ways:
    + Fuel type
    + PUN identification
    + NOIE affiliation

Some observations:
    + Regarding the fuel type break down:
        + It’s not surprising to see that nuclear RNs have the lowest values—nuclear units have the most “predictable” output, so CRRs may not be as valuable for hedging (because there is simply not much volatility to expect).
        + The solar and renewables RNs prices have risen in recent months. Several of the high-priced CRR SPs in recent months in the Far West are classified with these fuel types, so it is not too surprising to see these fuel type lines on the rise. (For those curious, the difference between “renewable” and “solar” and “wind” is not subjective—it comes from an identification code in the MMS_MFMASTER.MF_DELIVERY_POINTS database table.)
        + One might have expected the wind-associated RNs to be higher relative to the other fuel type lines due to the volatility of wind generation and the potential “hedge value” to be gained by acquiring CRRs associated with these units. On the other hand, wind generation (along with nuclear generation) is at the bottom of the bid stack for generation dispatch, so perhaps the observation that the nuclear and wind RNs have the lowest prices is a reflection of this. Additionally, if the Off Peak TOU prices were to be isolated, I suspect that we would see a major difference in the relative position of the wind line.
    + Regarding the PUN graph, there is a non-trivial difference between the two lines (PUN and not PUN). This might have been expected because PUN sites are different from other generation sites in many ways. 
    + Regarding the NOIE affiliation plot, there does not seem to be much difference between the two types (NOIE-owned or not NOIE-owned). I’m not sure if anyone would have expected that there would be a difference between the two, but nonetheless, it is something that is worthwhile to consider.

One thing that is apparent in all the plots shown above is a general trend upwards. While one may interpret this to mean that CRR prices in general are increasing, I do not think that this case. By my interpretation, this “phenomenon” is just a consequence of the choice of reference point. In other words, prices are only increasing relative to the reference point(s) (i.e. STP_STP_G1 and STP_STP_G2), but this does not indicate anything directly about all prices in general. My point can be proven (albeit, somewhat “imprecisely”) by breaking down the prices into tiers, as shown below.


Takeaways:
    + The stability evident in the profile of the middle tier indicates that the median price (and prices near around it) has generally stayed the same over time.
    + The prices outside of the middle third have become exaggerated as time has passed. This indicates that price magnitudes have increased in both directions, not just the positive direction (although the prices in the upper third have increased in magnitude more drastically than those in the bottom third). This observation reflects the more aggressive bidding behavior and higher clearing prices that we have seen in recent CRR auctions.

###  CRR Price Trends

Finally, I wanted to look at “trends” among individual CRR SPPs. Which SPs are trending up and trending down in terms of price?

A couple of notes about my approach here:
+ As a means of identifying/quantifying trend, I used the coefficient estimate for SP-specific regression models using date as the lone predictor of price. (This approach represents a modified form of time-series modeling.)
+ A positive coefficient estimate indicates a trend up, and a negative estimate indicates a trend down. The coefficient estimate is represented by slope of the regression line.

The following visual shows the data and regression lines for a select set of CRR SPs.

And, to supplement the above plot, the following one aggregates over all CRR SPs in each tier.

It’s difficult to draw any definitive conclusions about singular CRR SPs from this evaluation. Nonetheless, it is useful to visualize the volatility/stability of prices for individual SPs over time.

Some observations for the SPs shown in the first of the two visuals above:
    + There is no obvious relationship between the fuel type of the RNs shown and their trend tier. (For example, there are wind-associated RNs in each tier.)
    + There seems to be some relationship between the zones of the SPs and their tiers.
        + HOVEY_GEN and LASSO_GEN are both trending up and are in the Far West.
        + The five SPs shown in the mid third are in the West.
        + DERMOT_ALL and FLUVANNA_1_2 are both trending up and are in the Panhandle.
        + DOWGEN_PUN1 and BSF_PUN1 are both trending down and are near Houston. 
On the other hand, one might argue that these apparent relationships are just an indication that prices of SPs that are close geographically are likely to have similar prices and price trends.

##  CONCLUSION

Hopefully this analysis is useful for understanding relationships among the three market and for phenomena in the CRR market in particular. While trying to gain insight about the CRR market by investigating CRR point-to-point prices is certainly more conventional, attempting to evaluate singular point prices can offer a more direct interpretation of trends—especially geo-spatial trends. (On the other hand, one might consider this approach inaccurate because there is “no such thing” as CRR SPPs.)

As a final note, I would like to say that all of this is easily reproducible, so if anyone would like to see something different (e.g. different settings for color gradients, etc.), it would not be difficult to do so."

## Follow-up

I was interested in how the data looks going back farther in time. (The CRR-specific graphs below only look at the past 12 months.) Here I reproduce the first correlation graph and all of the graphs in the CRR section with CRR Monthly auction data going back to 2013. These graphs are useful for contextualizing/validating some of what I discussed in my initial email. 


    + When looking only at the last 12 Monthly auctions (as was done in the previous email), it might seem that high correlations are highly likely. However, when going back further in time and reviewing more data (as is done here), it is apparent that this was not always the case.
    + In specific, the CRR- RTM correlations were weak in many month-TOU combinations prior to 2016.
    + The CRR-DAM correlations were weak in several pre-2016 months, most commonly in the OP hours.
    + The DAM-RTM correlations were weak in several pre-2016 months, most commonly in the PWE hours.

    + The improvement in correlations since 2016 could be attributed to a number of factors, including:
        + “Smarter” and/or more consistent MP behavior.
        + More accurate/consistent modeling by either/both of the CRR and Network Modeling teams.
        + Smaller effect of forced outages (causing discrepancies between each market’s topology).

I think the first of these points is probably the most true, although it’s hard to know for sure. I would like to think that the second point is true, but that’s difficult to prove as well. The last of these factors would be difficult to quantify, but, if it can be shown to be possible, it would be worthwhile to investigate.

In addition to the factors described above, one might hypothesize that the CRR team has become better at selecting worst outage dates and/or there have been more submissions of outages to incorporate in the CRR models (which, theoretically, should the CRR model more accurate). However, some of the analysis I have done in the past does not indicate that this is the case.

    + The impact of the CREZ transmission projects—which facilitated the export of wind generation from the WEST and reduced curtailment of these resources in real time—is very apparent when reviewing the data back to the beginning of 2013. In particular, the high CRR prices throughout 2013 in the WEST reflect the re-occurring congestion in the zone prior to the completion of the projects near the end of that year. This year, the WEST prices rose again due to congestion arising for similar reasons.

    + Again, the WEST prices stand out here.
    + The notion that “LZ price > RN price > HB price” holds true, as was pointed out before.

    + We see some of the same trends with this fuel type plot as those apparent in my initial email:
        + Volatility with the solar and renewable data, relative to the rest.
        + Low prices for nuclear and high prices for CT (simple and combined), relative to the rest. This generally reflects the bid stack for generation dispatch in the RTM.

    + When just looking at the PUN and non-PUN profiles for the past 24 months compared to all months since 2013, it is clear that the difference between the two has become non-trivial recently (approximately since the midpoint of 2016). Actually, even before then, the two lines seem fairly dissimilar (i.e. one line goes up while the other either goes down or stays relatively the same).

    + As was seen in my initial email, the data for having and not having a NOIE LZ affiliation indicates that the difference between the two is insignificant.

    + The graph above back up my point(s) from before—that the median price (and the middle tier of prices) has stayed relatively constant over time, while prices in general have increased in magnitude in both the positive and negative direction.

    + All of the points identified by my regression analysis for largest change in price over time are different from before. I believe that this is primarily due to the difference in sample size—50+ Monthly auctions compared to only 12.
    + Interestingly, a good number of the points shown here do not have prices for all of the auctions evaluated. This reflects the fact that these points either were created sometime after 2013 (e.g. LV3_RN and SPLAIN1_RN) or have been retired (e.g. NTX_NTX_123 and KUNI_LGE_NWP). While one might be tempted to draw some conclusions about these SPs, it’s difficult to do so since these new and retired points are dispersed among the three tiers. (For example, although both LV3_RN and SPLAIN1_RN were created after 2013, the former is in the “top third” and the latter is in the “bottom third”, so it would be foolish to conclude anything about new points in general.) As with the previous email, it’s difficult to make any strong deductions about the SPs shown here. Nonetheless, it’s instructive to see the trends in the prices with these “extreme” sets of points. 

    + While the middle tier was trending up in the previous version of this plot, expanding the time range shows the middle tier trending slightly down overall (since 2013). This trend backs up my prior point that prices have increased relative to the reference SPPs (for STP_STP_UNIT1 and STP_STP_UNIT2) in the past year.

# Reference: "January 2018 Revenue Neutrality Allocation" Presentation given by Dave Maggio on 2/28/2018 for WMS

## High Revenue Neutrality Allocation (RENA)

### Components

    + Energy Imbalance Payments or Charges (RTEIAMTTOT)
    + Payments for Block Load Transfers (BLTRAMTTOT)
    + Payments for DC Tie Imports (RTDCIMPAMTTOT)
    + Charges for DC Tie Exports (RTDCEXPAMTTOT)
    + Congestion Payments or Charges for Self-Schedules (RTCCAMTTOT)
    + Payments or Charges for PTP Obligations (RTOBLAMTTOT)
    + Payments for PTP Obligations with Links to Options (RTOBLLOAMTTOT)

### Drivers

+ Significant Real-Time Market (RTM) congestion cost combined with other factors can lead to high RENA amounts.
    + “Over-selling” of transmission in the Day-Ahead Market (DAM)
        + Differences in topology between DAM and real-time (e.g., a forced outage of transmission equipment)
        + Inaccurate load distribution factors
    + Application of the -$251/MWh price floor to real-time Settlement Point Prices (SPPs)
    + Modeling of PTP Obligations with Links to Options

### Examples

+ SPP price floor of -$251/MWh
    + The RTM Locational Marginal Price (LMP) is -$500/MWh
    + The RTM injection at the Settlement Point is 120 MW for 1 hour
    + The DAM injection at the Settlement Point is 100 MW for 1 hour
    + The energy imbalance collected is (100-120 MW) * -$251/MWh * 1 hour = $5,020 when it would have been $10,000 without the floor
    
+ Modeling of PTP Obligations with Links to Options
    + There is a PTP Obligation with a Link to an Option of 100 MW from Resource A to Load Zone 1 for 1 hour
    + The RTM prices at Resource A and Load Zone 1 are $100/MWh and $30/MWh, respectively
    + The 100 MW * ($100/MWh - $30/MWh) * 1 hour = $7,000 is not available to offset the payment of other transactions


# Reference: "Revisions to the LDF Methodology: Analysis for Method of Calculating PUN LDFs" Presentation given by Agee Springer on 9/6/2017 for WMS

## Background – LDF Methodology Change

+ Triggers for LDF updates:
    + Regular seasonal updates
    + Load model changes with a database load
    + Significant PUN net consumption changes due to its Resource outages
    + Significant Block Load Transfer (BLT) of load into the ERCOT system.

+ New process for PUN loads:
    + Based on historical data of the net power consumption at the PUN
    + Hourly average value of the net power consumption as the initial net load distribution at the PUN level
    + The net load distribution at the PUN level is further distributed to the individual loads inside the PUN
    
# Reference: "Review of High RENA events after NPRR831 Implementation" Presentation given by Jian Chen on //2018 for WMS

## Introduction

    + This presentation is focused on the discussion around NPRRs 831 and 832, specifically whether we’ve observed high amounts of RENA associated with PUN LDFs.

    + Based on our study, while there have been days high RENA it is unlikely PUN LDFs played a significant role.

## History of NPRR831

    + It was observed that missing PUN net load in Real-Time Load Zone price calculation and Load Distribution Factors (LDF) in Day-ahead market caused high RENA (Real-Time Revenue Neutrality Amount).
        + Missing PUN net loads in RT LZ price calculation could cause less Revenue collected when PUN net loads have high prices (PUN resource nodes has helping shift factor for high shadow price constraint).
        + Missing PUN LDF in DAM could cause the RT constraint to be oversold in DAM when PUN loads worsen the constraint but not modeled in DAM models (PUN resource nodes has helping shift factor for the constraint).
    + NPRR831 was then implemented to include PUN net loads into Real-time Load Zone price calculation, and include PUN LDFs in Day-ahead Market. 
    + During the discussion of NPRR831, the concern was that the inaccuracy of PUN LDFs could still cause DAM oversold problem. Assuming large error does happen on certain PUN LDFs, two conditions still need to be met in order to cause significant RENA
        + High Real-Time congestion rent on the constraint
        + The PUN load with errors has significant shift factor on the constraint

## Summary

    + Since NPRR831 got implemented on 11/02/17, there have been 4 days with high RENA.
    + The top constraints on those days were reviewed by examining their DAM oversold amount and the possible causes of oversold.
    + Based on study, it is unlikely PUN LDFs played a significant role in the cause of high RENA.