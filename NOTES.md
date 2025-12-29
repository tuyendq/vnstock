

## TCBS API Discontinuation
As of December 15, 2025, TCBS has discontinued access to their public API. Users seeking to retrieve stock price data can utilize the VNDIRECT API as an alternative.  
From 15/12/2025 cannot access public TCBS API anymore.


Source: https://github.com/phamdinhkhanh/vnquant/issues/6
```python
def crawl_one_symbol(symbol, start_date, end_date):
        API_VNDIRECT = 'https://finfo-api.vndirect.com.vn/v4/stock_prices/'
        query = 'code:' + symbol + '~date:gte:' + start_date + '~date:lte:' + end_date
        delta = datetime.strptime(end_date, '%Y-%m-%d') - datetime.strptime(start_date, '%Y-%m-%d')
        params = {
            "sort": "date",
            "size": delta.days + 1,
            "page": 1,
            "q": query
        }
        res = requests.get(API_VNDIRECT, params=params)
        data = res.json()['data']
        return data
```

https://finfo-api.vndirect.com.vn/v4/stock_prices/?q=code:SSi~date:gte:2023-10-16~date:lte:2023-10-17&sort=date

https://ping.vndirect.com.vn/

