# TD9--Automating-Trading-On-Binance

## Task list - GET

### Get all Crypotcurrencies on Binance Plateform
- Use this URL ```https://api.binance.com/api/v1/exchangeInfo``` to get all cryptocurrencies on this plateform
- ```list(dict.fromkeys(#YourList))``` use this function to remove all duplicate
- On Notebook, ```getListCrypto()```

### Get Asks and Bids from a pair
-Use this URL ```'https://api.binance.com/api/v3/depth``` to get all orderbook for a pair
- Give your symbol
- In return, your have a JSON with asks values and bids values. You can filter.
- On Notebook, ```getDepth(direction='asks',pair='BTCUSDT') getOrderBook(pair='BTCUSDT')```

### Get Candle from a pair
-Use this URL ```https://api.binance.com/api/v3/klines``` to get 500 lastest data
- Give your symbol
- On Notebook, ```refreshDataCandle(pair='BTCUSDT',duration='5m')```

### Use SQLITE to stock and share data
- ```createTable(pair)``` => create a new table with name your pair ex:BTCETH
- ```getindex(pair)``` => return the last index in a pair table
- ```getLastDate(pair)``` and ```getAvailableData(pair, List)``` => return a List which old data are delected (old timestamp)
- ```StorecandlModify(pair,List)``` => Update in database
- ```refreshData(pair='BTCUSDT')``` => extract values in database
- ```dropTable(pair='BTCUSDT')``` => delete database

## Task list - POST

### requirement
if you have this problem => ```"Binance error: Timestamp for this request is 1000ms ahead of the server's time"```
- Windows Start > Command Prompt (right click and run as administrator)
```command
> net stop w32time
> w32tm /unregister
> w32tm /register
> net start w32time
> w32tm /resync
```

### create an order in Binance
- ```createOrderTable()``` => give a database with your own orders
- ```AddOrder(uuid,symbol,quantity,price,timestamp,side)``` => add new order in database
- ```createOrder(api_key="",secret_key="",direction='SELL',price=0,amount=0,pair='XTZUSDT',orderType='LIMIT')``` => send order in Binance and add this order in database

### canceled an order in Binance
- ```findOrder(uuid)``` => get values for cancel
- ```delOrder(uuid)``` => delete order in database
- ```cancelOrder(api_key, secret_key, uuid)``` => delete Order from Binance and in your database








