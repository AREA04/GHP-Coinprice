---
title: Coinprice Workflows
permalink: /docs/workflows/
---

Coinprice takes advantage of a wide array of data providers to provide you with an easy-to-use solution for your price conversion needs. You can make calls to our RESTful API to provide immediate data for your applications needs. Here are a few workflows that can be accomplished by users interacting with our API.

### View a crypto's price in several other currencies

Your developing a cryptocurrency application that you need to apply conversion calculation on for Ethereum. You tried doing manually but you found that parsing the market values and calculating the outcomes was strenuous work. You stumble accros Coinprice, which promises to easily solve your problem.

1. Send a request to the `GET` https://api.payrollrecord.com/price endpoint. Your request must include the `from` cryptocurrency as a query parameter. Here's the complete request in cURL:

	```
	curl --request GET \
		--url 'https://crypto-price.p.rapidapi.com/price?from=ETH' \
		--header 'X-RapidAPI-Host: crypto-price.p.rapidapi.com' \
		--header 'X-RapidAPI-Key: {Your RapidAPI key}'
	```

2. The JSON object in the response will contain the conversion rates for [`USD`, `BTC`, `EUR`, `JPY`, `AUD`, `CAD`, `CHF`, `CNY`, `GBP`] if no `to` parameter is defined. The response will look as follows

	```
	{
		"USD":3502.63
		"BTC":0.07611618255818679
		"EUR":3169.04
		"JPY":429538.1745430282
		"AUD":4662.11
		"CAD":4381.62
		"CHF":3243.37
		"CNY":22287.94
		"GBP":2669.88
	}
	```

### View a several crypto prices in several other currencies

You have been using Coinprice for a bit now and you really like the simplicity. You have evolved your app to support 4 different cryptocurrencies now and you are tired of making four seperate calls to the API for your pricing data. But you're finding that you only need the converstion for BTC, USD, AUD, XRP

1. Send a request to the `GET` https://api.payrollrecord.com/prices endpoint. Your request must include the `from` cryptocurrency as a query parameter. Here's the complete request in cURL:

	```
	curl --request GET \
		--url 'https://crypto-price.p.rapidapi.com/prices?from=BTC%2C%20doge%2C%20eth&to=usd%2C%20bitcoin%2C%20AUD%2C%20XRP' \
		--header 'X-RapidAPI-Host: crypto-price.p.rapidapi.com' \
		--header 'X-RapidAPI-Key: {Your RapidAPI key}'
	```

2. The JSON object in the response will contain the conversion rates for [`USD`, `BTC`, `EUR`, `JPY`, `AUD`, `CAD`, `CHF`, `CNY`, `GBP`] if no `to` parameter is defined. The response will look as follows

	```
	{
		"BTC" : {
		"USD":46087.65
		"BTC":1
		"AUD":61344.05
		"XRP":55319.955701937244
		}
		"doge" : {
		"USD":0.15
		"BTC":0.0000032596726984374647
		"AUD":0.2
		"XRP":0.18004809000438482
		}
		"eth" : {
		"USD":3502.63
		"BTC":0.07611618255818679
		"AUD":4662.11
		"XRP":4204.278943280389
		}
	}
	```