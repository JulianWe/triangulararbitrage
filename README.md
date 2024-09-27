# triangulararbitrage
Triangular Arabitrage on Binance API

**0. Triangular Arbitrage**
```python
import requests

# API-URLs für drei Währungspaare auf Binance
url = 'https://api.binance.com/api/v3/ticker/price'

def get_prices():
    response = requests.get(url)
    return {item['symbol']: float(item['price']) for item in response.json()}

def check_triangular_arbitrage():
    prices = get_prices()

    # Beispiel: BTC/USDT, ETH/USDT, ETH/BTC
    btc_usdt = prices['BTCUSDT']
    eth_usdt = prices['ETHUSDT']
    eth_btc = prices['ETHBTC']

    # Berechnung der Arbitragemöglichkeiten
    if (btc_usdt * eth_btc) < eth_usdt:
        print("Arbitrage-Möglichkeit gefunden: BTC -> ETH -> USDT")
    elif (eth_usdt / eth_btc) < btc_usdt:
        print("Arbitrage-Möglichkeit gefunden: ETH -> BTC -> USDT")

if __name__ == "__main__":
    check_triangular_arbitrage()

```




**1. Arbitrage zwischen Binance und Kraken**
```python
import requests

# API-URLs
binance_url = 'https://api.binance.com/api/v3/ticker/price?symbol=BTCUSDT'
kraken_url = 'https://api.kraken.com/0/public/Ticker?pair=BTCUSD'

def get_binance_price():
    response = requests.get(binance_url)
    return float(response.json()['price'])

def get_kraken_price():
    response = requests.get(kraken_url)
    return float(response.json()['result']['XXBTZUSD']['c'][0])

def check_arbitrage():
    binance_price = get_binance_price()
    kraken_price = get_kraken_price()

    print(f"Binance Price: {binance_price}, Kraken Price: {kraken_price}")

    if binance_price < kraken_price:
        print("Kaufsignal auf Binance, Verkaufsignal auf Kraken")
        # Hier Kauf und Verkauf implementieren
    elif kraken_price < binance_price:
        print("Kaufsignal auf Kraken, Verkaufsignal auf Binance")
        # Hier Kauf und Verkauf implementieren

if __name__ == "__main__":
    check_arbitrage()
```



**2. Arbitrage zwischen Binance und Bitfinex**
```python

import requests

# API-URLs
binance_url = 'https://api.binance.com/api/v3/ticker/price?symbol=BTCUSDT'
bitfinex_url = 'https://api.bitfinex.com/v1/pubticker/btcusd'

def get_binance_price():
    response = requests.get(binance_url)
    return float(response.json()['price'])

def get_bitfinex_price():
    response = requests.get(bitfinex_url)
    return float(response.json()['last_price'])

def check_arbitrage():
    binance_price = get_binance_price()
    bitfinex_price = get_bitfinex_price()

    print(f"Binance Price: {binance_price}, Bitfinex Price: {bitfinex_price}")

    if binance_price < bitfinex_price:
        print("Kaufsignal auf Binance, Verkaufsignal auf Bitfinex")
        # Hier Kauf und Verkauf implementieren
    elif bitfinex_price < binance_price:
        print("Kaufsignal auf Bitfinex, Verkaufsignal auf Binance")
        # Hier Kauf und Verkauf implementieren

if __name__ == "__main__":
    check_arbitrage()
```



**3. Arbitrage zwischen Kraken und Bitfinex**
```python
import requests

# API-URLs
kraken_url = 'https://api.kraken.com/0/public/Ticker?pair=BTCUSD'
bitfinex_url = 'https://api.bitfinex.com/v1/pubticker/btcusd'

def get_kraken_price():
    response = requests.get(kraken_url)
    return float(response.json()['result']['XXBTZUSD']['c'][0])

def get_bitfinex_price():
    response = requests.get(bitfinex_url)
    return float(response.json()['last_price'])

def check_arbitrage():
    kraken_price = get_kraken_price()
    bitfinex_price = get_bitfinex_price()

    print(f"Kraken Price: {kraken_price}, Bitfinex Price: {bitfinex_price}")

    if kraken_price < bitfinex_price:
        print("Kaufsignal auf Kraken, Verkaufsignal auf Bitfinex")
        # Hier Kauf und Verkauf implementieren
    elif bitfinex_price < kraken_price:
        print("Kaufsignal auf Bitfinex, Verkaufsignal auf Kraken")
        # Hier Kauf und Verkauf implementieren

if __name__ == "__main__":
    check_arbitrage()

```

**5. Arbitrage zwischen Huobi und Binance**
```python
import requests

# API-URLs
huobi_url = 'https://api.huobi.pro/market/detail/merged?symbol=btcusdt'
binance_url = 'https://api.binance.com/api/v3/ticker/price?symbol=BTCUSDT'

def get_huobi_price():
    response = requests.get(huobi_url)
    return float(response.json()['tick']['close'])

def get_binance_price():
    response = requests.get(binance_url)
    return float(response.json()['price'])

def check_arbitrage():
    huobi_price = get_huobi_price()
    binance_price = get_binance_price()

    print(f"Huobi Price: {huobi_price}, Binance Price: {binance_price}")

    if huobi_price < binance_price:
        print("Kaufsignal auf Huobi, Verkaufsignal auf Binance")
    elif binance_price < huobi_price:
        print("Kaufsignal auf Binance, Verkaufsignal auf Huobi")

if __name__ == "__main__":
    check_arbitrage()

```

**6. Arbitrage zwischen Coinbase und Kraken**
```python
import requests

# API-URLs
coinbase_url = 'https://api.coinbase.com/v2/prices/spot?currency=USD'
kraken_url = 'https://api.kraken.com/0/public/Ticker?pair=BTCUSD'

def get_coinbase_price():
    response = requests.get(coinbase_url)
    return float(response.json()['data']['amount'])

def get_kraken_price():
    response = requests.get(kraken_url)
    return float(response.json()['result']['XXBTZUSD']['c'][0])

def check_arbitrage():
    coinbase_price = get_coinbase_price()
    kraken_price = get_kraken_price()

    print(f"Coinbase Price: {coinbase_price}, Kraken Price: {kraken_price}")

    if coinbase_price < kraken_price:
        print("Kaufsignal auf Coinbase, Verkaufsignal auf Kraken")
    elif kraken_price < coinbase_price:
        print("Kaufsignal auf Kraken, Verkaufsignal auf Coinbase")

if __name__ == "__main__":
    check_arbitrage()


```



**7. Arbitrage zwischen Bittrex und Binance**
```python
import requests

# API-URLs
bittrex_url = 'https://api.bittrex.com/v3/markets/BTC-USDT/ticker'
binance_url = 'https://api.binance.com/api/v3/ticker/price?symbol=BTCUSDT'

def get_bittrex_price():
    response = requests.get(bittrex_url)
    return float(response.json()['lastTradeRate'])

def get_binance_price():
    response = requests.get(binance_url)
    return float(response.json()['price'])

def check_arbitrage():
    bittrex_price = get_bittrex_price()
    binance_price = get_binance_price()

    print(f"Bittrex Price: {bittrex_price}, Binance Price: {binance_price}")

    if bittrex_price < binance_price:
        print("Kaufsignal auf Bittrex, Verkaufsignal auf Binance")
    elif binance_price < bittrex_price:
        print("Kaufsignal auf Binance, Verkaufsignal auf Bittrex")

if __name__ == "__main__":
    check_arbitrage()


```

**8. Arbitrage zwischen OKEx und Binance**
```python
import requests

# API-URLs
okex_url = 'https://www.okex.com/api/spot/v3/instruments/BTC-USDT/ticker'
binance_url = 'https://api.binance.com/api/v3/ticker/price?symbol=BTCUSDT'

def get_okex_price():
    response = requests.get(okex_url)
    return float(response.json()['last'])

def get_binance_price():
    response = requests.get(binance_url)
    return float(response.json()['price'])

def check_arbitrage():
    okex_price = get_okex_price()
    binance_price = get_binance_price()

    print(f"OKEx Price: {okex_price}, Binance Price: {binance_price}")

    if okex_price < binance_price:
        print("Kaufsignal auf OKEx, Verkaufsignal auf Binance")
    elif binance_price < okex_price:
        print("Kaufsignal auf Binance, Verkaufsignal auf OKEx")

if __name__ == "__main__":
    check_arbitrage()

```

**9. Arbitrage zwischen KuCoin und Binance**
```python

import requests

# API-URLs
kucoin_url = 'https://api.kucoin.com/api/v1/prices'
binance_url = 'https://api.binance.com/api/v3/ticker/price?symbol=BTCUSDT'

def get_kucoin_price():
    response = requests.get(kucoin_url)
    return float(response.json()['data']['BTC'])

def get_binance_price():
    response = requests.get(binance_url)
    return float(response.json()['price'])

def check_arbitrage():
    kucoin_price = get_kucoin_price()
    binance_price = get_binance_price()

    print(f"KuCoin Price: {kucoin_price}, Binance Price: {binance_price}")

    if kucoin_price < binance_price:
        print("Kaufsignal auf KuCoin, Verkaufsignal auf Binance")
    elif binance_price < kucoin_price:
        print("Kaufsignal auf Binance, Verkaufsignal auf KuCoin")

if __name__ == "__main__":
    check_arbitrage()

```

**10. Arbitrage zwischen Bitstamp und Kraken**
```python
import requests

# API-URLs
bitstamp_url = 'https://www.bitstamp.net/api/v2/ticker/btcusd/'
kraken_url = 'https://api.kraken.com/0/public/Ticker?pair=BTCUSD'

def get_bitstamp_price():
    response = requests.get(bitstamp_url)
    return float(response.json()['last'])

def get_kraken_price():
    response = requests.get(kraken_url)
    return float(response.json()['result']['XXBTZUSD']['c'][0])

def check_arbitrage():
    bitstamp_price = get_bitstamp_price()
    kraken_price = get_kraken_price()

    print(f"Bitstamp Price: {bitstamp_price}, Kraken Price: {kraken_price}")

    if bitstamp_price < kraken_price:
        print("Kaufsignal auf Bitstamp, Verkaufsignal auf Kraken")
    elif kraken_price < bitstamp_price:
        print("Kaufsignal auf Kraken, Verkaufsignal auf Bitstamp")

if __name__ == "__main__":
    check_arbitrage()

```



**11. Arbitrage zwischen Binance und Gemini**
```python

import requests

# API-URLs
gemini_url = 'https://api.gemini.com/v1/pubticker/btcusd'
binance_url = 'https://api.binance.com/api/v3/ticker/price?symbol=BTCUSDT'

def get_gemini_price():
    response = requests.get(gemini_url)
    return float(response.json()['last'])

def get_binance_price():
    response = requests.get(binance_url)
    return float(response.json()['price'])

def check_arbitrage():
    gemini_price = get_gemini_price()
    binance_price = get_binance_price()

    print(f"Gemini Price: {gemini_price}, Binance Price: {binance_price}")

    if gemini_price < binance_price:
        print("Kaufsignal auf Gemini, Verkaufsignal auf Binance")
    elif binance_price < gemini_price:
        print("Kaufsignal auf Binance, Verkaufsignal auf Gemini")

if __name__ == "__main__":
    check_arbitrage()

```



**12. Arbitrage zwischen Huobi und OKEx**
```python
import requests

# API-URLs
huobi_url = 'https://api.huobi.pro/market/detail/merged?symbol=btcusdt'
okex_url = 'https://www.okex.com/api/spot/v3/instruments/BTC-USDT/ticker'

def get_huobi_price():
    response = requests.get(huobi_url)
    return float(response.json()['tick']['close'])

def get_okex_price():
    response = requests.get(okex_url)
    return float(response.json()['last'])

def check_arbitrage():
    huobi_price = get_huobi_price()
    okex_price = get_okex_price()

    print(f"Huobi Price: {huobi_price}, OKEx Price: {okex_price}")

    if huobi_price < okex_price:
        print("Kaufsignal auf Huobi, Verkaufsignal auf OKEx")
    elif okex_price < huobi_price:
        print("Kaufsignal auf OKEx, Verkaufsignal auf Huobi")

if __name__ == "__main__":
    check_arbitrage()


```


**Aggregated Arbitrage Script**
```python
import requests
import time

class ArbitrageBot:
    def __init__(self):
        self.bins = {
            'binance': {
                'url': 'https://api.binance.com/api/v3/ticker/price?symbol=BTCUSDT',
                'price_func': self.get_binance_price
            },
            'kraken': {
                'url': 'https://api.kraken.com/0/public/Ticker?pair=BTCUSD',
                'price_func': self.get_kraken_price
            },
            'bittrex': {
                'url': 'https://api.bittrex.com/v3/markets/BTC-USDT/ticker',
                'price_func': self.get_bittrex_price
            },
            'bitfinex': {
                'url': 'https://api.bitfinex.com/v1/pubticker/btcusd',
                'price_func': self.get_bitfinex_price
            },
            'okex': {
                'url': 'https://www.okex.com/api/spot/v3/instruments/BTC-USDT/ticker',
                'price_func': self.get_okex_price
            },
            'gemini': {
                'url': 'https://api.gemini.com/v1/pubticker/btcusd',
                'price_func': self.get_gemini_price
            },
            'huobi': {
                'url': 'https://api.huobi.pro/market/detail/merged?symbol=btcusdt',
                'price_func': self.get_huobi_price
            }
        }

    def get_binance_price(self):
        response = requests.get(self.bins['binance']['url'])
        return float(response.json()['price'])

    def get_kraken_price(self):
        response = requests.get(self.bins['kraken']['url'])
        return float(response.json()['result']['XXBTZUSD']['c'][0])

    def get_bittrex_price(self):
        response = requests.get(self.bins['bittrex']['url'])
        return float(response.json()['lastTradeRate'])

    def get_bitfinex_price(self):
        response = requests.get(self.bins['bitfinex']['url'])
        return float(response.json()['last'])

    def get_okex_price(self):
        response = requests.get(self.bins['okex']['url'])
        return float(response.json()['last'])

    def get_gemini_price(self):
        response = requests.get(self.bins['gemini']['url'])
        return float(response.json()['last'])

    def get_huobi_price(self):
        response = requests.get(self.bins['huobi']['url'])
        return float(response.json()['tick']['close'])

    def check_arbitrage(self):
        prices = {exchange: info['price_func']() for exchange, info in self.bins.items()}
        print(prices)

        # Arbitrage-Logik
        for exchange_a, price_a in prices.items():
            for exchange_b, price_b in prices.items():
                if exchange_a != exchange_b:
                    if price_a < price_b:
                        print(f"Arbitrage-Möglichkeit: Kaufe auf {exchange_a}, verkaufe auf {exchange_b}")

    def run(self):
        while True:
            self.check_arbitrage()
            time.sleep(10)  # Warte 10 Sekunden zwischen den Überprüfungen

if __name__ == "__main__":
    bot = ArbitrageBot()
    bot.run()


```


**Arbitrage-Trading-Bot mit zusätzlichen Strategien und Indikatoren**
```python
import requests
import time
import pandas as pd
import numpy as np

class TradingBot:
    def __init__(self):
        self.symbol = 'BTCUSDT'
        self.interval = '1h'  # Zeitintervall für die Kerzen
        self.prices = []

    def fetch_data(self):
        url = f'https://api.binance.com/api/v3/klines?symbol={self.symbol}&interval={self.interval}&limit=100'
        response = requests.get(url)
        data = response.json()
        self.prices = pd.DataFrame(data, columns=['Open Time', 'Open', 'High', 'Low', 'Close', 'Volume', 
                                                  'Close Time', 'Quote Asset Volume', 'Number of Trades', 
                                                  'Taker Buy Base Asset Volume', 'Taker Buy Quote Asset Volume', 
                                                  'Ignore'])
        self.prices['Close'] = self.prices['Close'].astype(float)

    def calculate_indicators(self):
        self.prices['SMA_20'] = self.prices['Close'].rolling(window=20).mean()
        self.prices['SMA_50'] = self.prices['Close'].rolling(window=50).mean()
        self.prices['EMA_20'] = self.prices['Close'].ewm(span=20, adjust=False).mean()
        self.prices['RSI'] = self.calculate_rsi(self.prices['Close'], 14)

    def calculate_rsi(self, series, period):
        delta = series.diff(1)
        gain = (delta.where(delta > 0, 0)).rolling(window=period).mean()
        loss = (-delta.where(delta < 0, 0)).rolling(window=period).mean()
        rs = gain / loss
        rsi = 100 - (100 / (1 + rs))
        return rsi

    def check_signals(self):
        latest_data = self.prices.iloc[-1]
        signals = []

        # SMA Crossover Strategy
        if latest_data['SMA_20'] > latest_data['SMA_50']:
            signals.append('Buy Signal from SMA Crossover')
        elif latest_data['SMA_20'] < latest_data['SMA_50']:
            signals.append('Sell Signal from SMA Crossover')

        # RSI Strategy
        if latest_data['RSI'] < 30:
            signals.append('Buy Signal from RSI')
        elif latest_data['RSI'] > 70:
            signals.append('Sell Signal from RSI')

        return signals

    def run(self):
        while True:
            self.fetch_data()
            self.calculate_indicators()
            signals = self.check_signals()
            print(signals)
            time.sleep(60)  # Warte 60 Sekunden zwischen den Überprüfungen

if __name__ == "__main__":
    bot = TradingBot()
    bot.run()


```
