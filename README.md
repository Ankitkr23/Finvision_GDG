 FINVISION :

1) Use Requests, Selenium Web Driver, Beautiful Soup, and Scrapy to web scrape data of Nifty50 Stocks 
      Containing PE, EPS, 52 Week High/Low, Lower and Upper Circuit, LTP, and Market Cap   
 , Volume, % Change, and convert to DataFrame.
Link- https://www.nseindia.com/
https://www.screener.in/company/
These are sites from which you can scrape the data of stocks.

Also, Add 6-month, 1-year, and 5-year returns in DataFrame .{Hint*- Use Yahoo Finance Library for loading OHLCV data of Nifty50 Stocks and find returns using Close or AdjClose Price.}

2) Use the T score, Z score, and confidence interval and plot Probability Distributions(Any) of the Daily volume, Daily Close Price, and Daily Returns of Any Stock.
The same applies to data: Use Yahoo Finance Library!

Bonus-
Find any two stocks using 2023-2024 data, which are stationary or non-stationary (Read about KPSS and ADF Test Time Series Analysis  )!



FINAL ASSIGNMENT

One day,Jindal Global Securities ltd Researchers were boring and planning something new for BTCUSD asset trading.Generally Strategies(technical indicators)  work on trending,momentum market .They were planning new something different.
So,they got an idea to use Stock Span Idea (The stock span problem is a financial problem where we have a series of daily price quotes for a stock denoted by an array arr[] and the task is to calculate the span of the stock’s price for all days. 
The span of the stock’s price on ith day represents the maximum number of consecutive days leading up to ith day (including the current day) where the stock’s price was less than or equal to its price on day i.) 
Momentum-Based Trading
A high stock span value indicates strong bullish momentum, suggesting that buyers are in control.
A low stock span value suggests weak momentum, indicating that the stock has not been outperforming recent prices.
Strategy:
If the stock span is increasing over multiple periods, it suggests a strong uptrend → Consider long positions.
If the span remains consistently low, it suggests weak price action → Avoid long trades or consider shorting.
2. Trend Confirmation & Breakout Strategy
Stocks with increasing stock span values show that price is making higher highs, confirming a strong trend.
Used with moving averages (e.g., 50-day, 200-day), the span can confirm whether an uptrend is genuine or just a short-term movement.
Strategy:
Identify a breakout when the span suddenly spikes, confirming a new trend initiation.
If span is low but suddenly jumps, it indicates a possible breakout.
3. Support & Resistance Detection
If the span increases before hitting a resistance level, it suggests strong bullish interest.
If the span decreases after reaching a support level, it indicates weakening buying pressure and possible reversal.
Strategy:
Use the span as a filter when trading breakouts or reversals at key levels.
A breakout with a high span value is more reliable.
4)If the stock span remains high for multiple days, it suggests prolonged bullish strength.
If the span suddenly drops, it can signal a potential reversal or that the stock has become overbought.
A very low stock span for multiple periods suggests selling exhaustion, meaning the stock might be oversold.
But they want to do using Stack (O(n) ) not in O(n^2) .
Assignment :-Now You have to code in C++ or Python using BTCUSD data (Yfinance daily data) .Analyze ,plot the result.


 2) In Stock market analysis, support levels are prices where a downtrend is expected to pause due to a concentration of demand, while resistance levels are prices where an uptrend is expected to pause due to a concentration of supply. You are tasked with building a system that dynamically updates with new stock prices and efficiently finds the local minima (support) and local maxima (resistance) within a given range of historical data.
Task:
Given an initial list of stock prices, you must support the following operations efficiently:
Update Operation: Append a new price to the list (the list is growing over time).
Query Operation (Range Minima): Given a range [L, R], return the minimum price (support level) in that range.
(Optional) Query Operation (Range Maxima): Given a range [L, R], return the maximum price (resistance level) in that range.
Your solution should be designed to handle a large number of updates and queries in real-time.
Input Format:
The first line contains two integers, N and Q, representing the initial number of prices and the number of operations, respectively.
The second line contains N space-separated integers representing the initial stock prices.
The next Q lines describe operations in one of the following formats:
"U X" – Update operation: append the price X to the list.
"Q L R" – Query operation: return the minimum price in the range from index L to R (0-indexed).
"M L R" – (Optional) Query operation: return the maximum price in the range from index L to R (0-indexed).
Output Format:
For each query, output the corresponding minimum (or maximum) price on a new line.
Constraints:
1 ≤ N, Q ≤ 10⁵
0 ≤ Price ≤ 10⁹
For query operations, ensure that 0 ≤ L ≤ R < current length of the list.

Approach
1. Data Structure Selection
Segment Tree:
Use a segment tree to support both range minimum queries (for support levels) and range maximum queries (for resistance levels) with updates.
Time Complexity:
Update: O(log N)
Query: O(log N)
This efficiency is ideal for real-time data updates in a live trading system.
2. Building the Segment Tree
Initialization:
Build a segment tree using the initial list of prices.
Each node of the tree represents a segment of the array and stores:
Minimum value: for support detection.
Maximum value (if needed): for resistance detection.
3. Handling Updates
Dynamic Growth:
When a new price is added, you can either:
Rebuild the tree incrementally: Expand the segment tree by adding new leaves as needed.
Or use a dynamic segment tree that supports an increasing number of elements.
Update the tree at the leaf corresponding to the new index and then update its ancestors.
4. Querying the Tree
Range Queries:
To determine support, query the segment tree for the minimum value in the specified range [L, R].
For resistance, query for the maximum value in the same range.
Combine results if needed to get an overall picture of the price levels in the window.


Assignment:-
Task 2 :- You have to code and find using  RMQ problem  in BTC-USD data and trade basis on it ,analyze ,use other indicators with this.

