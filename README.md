# CB-API-Robots
Simple robots for interacting with the CryptoBridgeProClass including Open a Market, Limit, Stop, and StopLimit order. Modify order, cancel order and get your Balance, Margin,PNL.

# Make an indicator 
Turn any [indicator into a signal](https://github.com/TradingToolCrypto/TradingTool-Wiki/wiki/Indicator-ADR#build-indicators-with-alerts-and-global-variables) for robots to make trades based on your signal alert.  
![Median channel](https://github.com/TradingToolCrypto/TradingTool-Wiki/blob/master/terminal64_Rls7DBxsBF.png)

## Setup the Robot Input Parameters  
- Setup the **CRYPTO BRIDGE** within the robot input tabs including your api key and api secret for the crypto exchange that you plan to trade.  
      - select the exchange  
      - select the market  
      - select the contract size  
      - select the Quote Precision digit ( not required if using market orders)  
      - select the Volume Precision digit (to properly normalize the contract size)  
![Add your settings](https://github.com/TradingToolCrypto/CB-API-Robots/blob/main/terminal64_txS6L7JxIu.png)  
## CB_OpenTradeRobot.mq5
This is a simple robot that places market orders on your crypto exchange account after finding a global variable made from your indicator. Once the robot finds the global variable that starts with **Signal** it will proceed with parsing the symbol to match the market that you want to trade. Once the match is complete, the robot will delete the global variable and place a market order on the exchange. 

### What to consider
Your indicator should make an alert global variable once per bar. The robot will delete this global variable once it has matched the appropiate market name.  CB Charts creates a unique market name such as BTCUSDT.bnf ( for binance futures), while the robot will trade on the exchange with the symbol BTCUSDT.  The **CB_OpenTradeRobot** will remove the suffix from the indicator's signal to match the appropiate market that you wish to trade.  
- CB Charts symbol is BTCUSDT.bnf  
- Robot trades on BTCUSDT  
- Robot parses BTCUSDT.bnf and matches with BTCUSDT, opens a position, and deletes the signal global variable  
- Indicator should only create an alert signal every new bar  
