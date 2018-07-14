### 야후 종가 크롤링 

```python
from pandas_datareader import data
import fix_yahoo_finance as yf
yf.pdr_override()
start_date = '2017-07-13'
tickers = ['067160.KQ', '035420.KS','000660.KS']
#아프리카tv와 네이버의 ticker(종목코드)
#아프리카는 코스닥, 네이버는 코스피
afreeca = data.get_data_yahoo(tickers[0], start_date)
naver = data.get_data_yahoo(tickers[1], start_date)
hinyx = data.get_data_yahoo(tickers[2], start_date)
```

### 한국거래소 종목코드 크롤링 

```python
import pandas as pd
code_df = pd.read_html('http://kind.krx.co.kr/corpgeneral/corpList.do?method=download&searchType=13', header=0)[0]
code_df.종목코드 = code_df.종목코드.map('{:06d}'.format)
code_df = code_df[['회사명','종목코드']]
code_df = code_df.rename(columns={'회사명':'name','종목코드':'code'})
code_df.head()
```
