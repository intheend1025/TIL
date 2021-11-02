# Javascript

AJAX, Asynchronous



#### AJAX

- Asynchronous javascript and xml
- 서버와 통신하기 위해 XMLHttpRequest 객체 활용
- 페이지 전체를 reload하지 않고서도 수행되는 '비동기성' (페이지 일부 업데이트)



#### Asynchronous JavaScript

- 자바스크립트는 single threaded이다. (이벤트 처리 Call Stack이 하나)
  - 비동기를 위해 즉시 처리못하는 이벤트 다른곳(web API)로 보내 처리하고
  - 처리된 이벤트 대기실 (Task queue)에 줄세워 놓고
  - call stack이 비면 담당자(event loop)가 대기줄에서 가장 오래된 이벤트를 call stack으로 보냄

-  동기식
  - 순차적, 직렬적 task 수행
  - 요청 보낸 후 응답 받아야만 다음 동작 수행(blocking)
- 비동기식
  - 병렬적 task 수행
  - 요청 보낸 후 응답 기다리지 않고 다음 동작 수행(non-blocking)
  - why 사용? 데이터 불러오는 동안 지속적 응답하는 화면 보여줌으로써 더욱 쾌적한 사용자 경험 제공
- 순차적인 비동기 처리
  - Async callbacks
  - promise-style
- 자바스크립트는 일급객체다. 
  - 다른 객체들에 적용할 수 있는 연산을 모두 지원하는 객체(함수)
  - 일급객체 조건
    - 인자로 넘길 수 있어야 함
    - 함수의 반환 값으로 사용할 수 있어야 함
    - 변수에 할당할 수 있어야 함



#### Callback Function

- 다른 함수에 인자로 전달된 함수
- Async callbacks
  - callback hell 발생할 수 있음 -> promise object 로 보완



#### Promise object

- 비동기 작업의 최종완료 또는 실패를 나타내는 객체
- Axios : 브라우저를 위한 Promise 기반 클라이언트
- 최신 : async & await 사용

```html
axios.get(URL)
	성공에 대한 약속
	.then(response => {
		return response.data
	}) 리턴 값은 아래 response로 들어감
	.then(response => {
		return response.title
	})
	실패에 대한 약속
	.catch(error => {
		console.log(error)
	})
	.finally(functions() {
		console.log('마지막에 무조건 시행')
	})
```



```javascript
// comment-form을 아이디값으로 가진 인자 추출
const commentForm = document.querySelector('#comment-form')
// submit 이벤트 발생 시 해당 함수 호출 및 실행
commentForm.addEventListener('submit', function (event) {
    // 실행해서 자기맘대로 끝내는거 방지
    event.preventDefault()
    // data-article-pk="{{ article.pk }}" 폼에 넣어준 데이터셋 가져오기
    const articlePk = event.target.dataset.articlePk
    // post 방식 csrf토큰 가져오기
    const csrftoken = document.querySelector('[name=csrfmiddlewaretoken]').value
    // 컨텐츠 내용 가져오기 (댓글 내용)
    const content = document.querySelector('[name=content]').value
	// ??
    const formData = new FormData()
    formData.append('content', content)
	// 프로미스 객체를 반환하는 post 요청 보내기
    axios({
      method: 'post',
      url: `/articles/${articlePk}/comments/`,
      data: formData,
      headers: { 'X-CSRFToken': csrftoken },
    })
      // 성공시 수행
      .then((res) => {
        // li 속성 만들어 내용 넣어주기
        const li = document.createElement('li')
        li.innerText = `${res.data.username} - ${res.data.content}`

        const ul = document.querySelector('ul')
        // ul의 자식 인자로 넣어주기
        ul.appendChild(li)

        // 댓글창 리셋
        event.target.reset()
      })
  })
```

