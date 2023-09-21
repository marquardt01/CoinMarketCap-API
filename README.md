# CoinMarketCap-API-Script
This script uses the CoinMarketCap API to fetch the current prices of cryptocurrencies
import requests 

def get_crypto_price(crypto_symbol):
    url = f'https://api.coinmarketcap.com/v1/ticker/{crypto_symbol}/'
    response = requests.get(url)
    data = response.json()
    if len(data) > 0 and 'price_usd' in data[0]:
        return float(data[0]['price_usd'])
    return None

# Usage example
crypto_symbols = ['bitcoin', 'ethereum', 'dogecoin']
for symbol in crypto_symbols:
    price = get_crypto_price(symbol)
    if price:
        print(f"Current price of {symbol.capitalize()}: ${price}")
    else:
        print(f"Failed to retrieve price for {symbol.capitalize()}")
