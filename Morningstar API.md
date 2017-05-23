## Credit to hahnicity

# Morningstar API

If you're interested in grabbing Morningstar data but cash strapped there are ways to do it without actually paying for it. 
## Historical Price API
The following URL will get you access to all available historical Morningstar price data for the Ford Corporation 

http://globalquote.morningstar.com/globalcomponent/RealtimeHistoricalStockData.ashx?ticker=F&showVol=true&dtype=his&f=d&curry=USD&range=1900-1-1|2014-10-10&isD=true&isS=true&hasF=true&ProdCode=DIRECT 

Now you will have every single daily piece of data for Ford between the dates of 01/01/1900 and 10/10/2014

## Real Time Quote API
For more fine grained data for current market activity you can call the real time quote API.

http://quotespeed.morningstar.com/quote.jsp?&jsoncallback=jQuery172017541670752689242_1441265385395&preAfter=1&ty=D&mtype=ST&exch=126&ticker=F&stype=1&days=5&_tid=1441265386097&ver=1.6.0&f=1&instid=MSRT&sdkver=2.1.20150320&qs_wsid=2D2114F870F6B844CDF8271C99BB8C7A&_=1441265386099

Which will give you all data for the Ford Corporation within the last 5 days. Included is data for intraday trading.

## Key Ratios
Get statistics for things like the following: Revenue, Net Income, Shares, Return on Equity, etc. all in CSV. For example;
if I wanted to get all of the key ratios for Facebook I could do something like

http://financials.morningstar.com/ajax/exportKR2CSV.html?t=FB
    
You can then get your favorite CSV library to read the data for you.

## Financials
Financial data for any ticker symbol you desire. Let's try Twitter (TWTR). First let's get the income statement

http://financials.morningstar.com/ajax/ReportProcess4CSV.html?t=TWTR&reportType=is&period=12&dataType=A&order=asc&columnYear=5&number=3

OK that's a lot of url parameters so let's break it down a bit:

 * reportType: is = Income Statement, cf = Cash Flow, bs = Balance Sheet
 * period: 12 for annual reporting, 3 for quarterly reporting
 * dataType: this doesn't seem to change and is always `A`
 * order: asc or desc (ascending or descending)
 * columnYear: 5 or 10 are the only two values supported
 * number: The units of the response data. 1 = None 2 = Thousands 3 = Millions 4 = Billions

So if we wanted to get the annual balance sheet information for TWTR we could request

http://financials.morningstar.com/ajax/ReportProcess4CSV.html?t=TWTR&reportType=bs&period=12&dataType=A&order=asc&columnYear=5&number=3
    
Likewise for Cash Flow;

http://financials.morningstar.com/ajax/ReportProcess4CSV.html?t=TWTR&reportType=cf&period=12&dataType=A&order=asc&columnYear=5&number=3
    
## Disclaimer

This is in no way an official API. As such it is not supported by Morningstar the organization. Furthermore, I would adviseto rate limit your downloads to be nice to Morningstar's servers. If not to be nice to Morningstar then to be kind to the other users of the unofficial API so as not to ruin a good thing.

## Future
More fine grained analysis on each parameter forthcoming besides some wonky URL. Also, analysis on the response data.


## Recommendations

http://quotes.morningstar.com/stockq/c-recommencation?&t=XNAS:MSFT&region=usa&culture=en-US&version=RET&cur=


