# BinanceTradingBot

To initialize TradingBot, you have to specify several parameters
- Symbol (e.g. BTCUSDT)
- Target Quantity (upper bounded by free balance)
- Period of Moving Average Line 1 (e.g. 3)
- Period of Moving Average Line 2 (e.g. 7)
- Candle Interval (e.g. 1 minute)
- Candle Size (e.g. 50)

After that, you can call StartAutoTrade to start auto trading, the flow is as below, for every 10 seconds
- Display account information
- Display open order
- Get candle data (since Candle Interval has minimum value of 1min but the bot loop every 10 seconds, so candle data is the same as previous one, no action will be done)
- Caluclate Moving Average of the latest 2 candles: CurrentCandle & PreviousCandle
- if (CurrentCandle Moving Average 1 > CurrentCandle Moving Average 2) AND (PreviousCandle Moving Average 1 < PreviousCandle Moving Average 2), then MA1 Cross above MA2, the bot then cancel Sell order & create New Buy order (current only support new market order)
- And if MA1 Cross below MA2, bot then cancel Buy order & create New Sell order (current only support new market order)
