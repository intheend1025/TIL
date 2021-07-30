# crawling

클라이언트는 URL통해 요청하고 서버는 문서(텍스트)를 응답한다

```python
import requests
from bs4 import BeautifulSoup

#요청을 보낼 URL
url = 'https://finance.naver.com/sise/'

#실제 요청을 보내고, 응답 객체를 response 변수에 저장
response = requests.get(url)

#응답 객체의 본문(text)을 해석하여 data 변수에 저장
data = BeautifulSoup(response.text, 'html.parser')

#해석한 data에서 원하는 정보를 선택하고, 내용만 kospi에 저장
kospi = data.select_one('#KOSPI_now').text


```



```python
import requests

url = 'https://api.agify.io?name=michael'

#응답 json str을 dict로 파싱해서 response에 저장
response = requests.get(url).json()

```