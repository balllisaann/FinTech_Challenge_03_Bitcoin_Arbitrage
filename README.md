# UW FinTech Challenge 3: Crypto Arbitrage
Author: Lisa Bailey, balllisaann@yahoo.com
Date: 9/5/2021
Contributing Authors: UW FinTech 21
Libraries used: 
- pandas
- pathlib (Path)
- mathplotlib

## Purpose of assignment
To use the 'pandas' library, a bit of plotting with the 'mathplotlib' library. 

Bitstamp and Coinbase prices were tracked from 1/1/2018 to 4/1/2018.  We were to look at the data to see if there were any opportunites for arbitrage and to calculate how much money could have been potentially made in by trades in that day if one share were bought every minute.

## Problems/Questions about the assignment

1. The "spread return" was only calculated if a profit would have been made.  But, in real life, we won't know if there will be a profit on the next buy/sell execution, so we will not be able to just filter for positive profits.  

'''
def spread_return(arbitrage_spread_period, date):
    return arbitrage_spread[arbitrage_spread > 0] / coinbase['Close'].loc[date]
'''

2. It is assumed that we know which cryptocurrency will be higher and which one will be lower and that this relationshiop will not change.  In real life, there is no reason that opportunities for arbitrage could not switch often.

'''
def arbitrage_spread(date) :
    return bitstamp['Close'].loc[date] - coinbase['Close'].loc[date]
'''

3. This exercise is based off of the assumption that a share would be purchased at the **close** price every minute.  If the minute is over and the close price is set, how do we execute a trade?  By executing a trade, doesn't that have the potential to *change* the close price?

4. The "fee" for a transaction is assumed to be 1% of the price of the lower asset that is being bought.  Is there no fee for selling the higher asset?

'''
def spread_return(arbitrage_spread_period, date):
    return arbitrage_spread_period[arbitrage_spread_period > 0] / **coinbase['Close'].loc[date]**

profitable_trades_early = spread_return_early[spread_return_early > .01]
'''

5. Again, we are filtering to only execute arbitrage on profits that are greater than 1% of the lower asset.  But, in real life, how will we know that the profit will be this threshold beforehand?

'''
profitable_trades_late = spread_return_late[spread_return_late > .01]
'''

6. When calculating the potential profit, the assumption seems to be that **one share** is being bought and sold at the close of each minute that meets the above thresholds in 1, 2 and 5 above.  In real life, I would hope that the user would have the choice to buy/sell a number of assets, or an amount of money.

## Conclusion
- There was a period in the early trading period where it looks like a significant profit could have been made, up to 350,000 USD.
- There was a period in the middle trading period where a minor profit of 10,000 USD could have been made.
- There was a period in the late trading period where no profit would have been made.