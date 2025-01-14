---
title: Javascript Promise 비동기함수
date: 2025-01-13 00:00:00 +09:00
categories: [Javascript, 문법]
tags:
  [
    Javascript,
    Promise,
    비동기함수수
  ]

---


## **<span style="color: steelblue; visibility: hidden;">Javascript Promise</span>**

### 1. Promise란?
- 자바스크립트는 **싱글 쓰레드**이다. 그래서 비동기를 동기식으로 처리하는 것이 필수적  
  이를 위해 콜백함수를 사용해왔는데 콜백함수의 단점인 콜백지옥으로 인해 코드의 가독성이 떨어지고 유지보수도
  힘들어 이를 해결하기 위해 **ES6**에서는 **Promise**가 표준 내장 객체로 추가됨  
- Promise는 비동기 작업을 동기 작업으로 처리하기 위한 객체  
  즉, Promise는 비동기 작업에 대하여, 비동기 작업이 완료된 후 결과 값 또는 실패의 이유를 콜백 함수(resolve,reject)로 전달한다.
- Promise는 3가지 상태값을 가지고 있다
	> **Pending(대기)** : 비동기 처리 로직이 아직 완료되지 않은 상태  
    **Fullfilled(이행)** : 비동기 처리가 완료되어 Promise가 결과값을 반환해준 상태(resolve()실행)  
    **Rejected(실패)** : 비동기 처리가 실패하거나 오류가 발생한 상태(reject()실행)
- Promise 객체의 메소드  
	> **then()**: 작업이 성공할 경우 실행할 콜백 함수를 등록한다  
    콜백함수의 반환값은  콜백함수에서 return키워드로 반환할수 있다  
    반환된값은 메소드 체인닝된 다음 then의 인자인 콜백함수의 인자로 받을 수 있다  
    참고로 then() 함수는 Promise객체를 반환한다

	> **catch()**: 작업이 실패할 경우 실행할 콜백 함수를 등록한다  
	> **finally()**: 작업이 성공하든 실패하든 마지막에 항상 실행할 콜백 함수를 등록한다

### 2. 예시
- Promise객체 사용
  Promise가 이행 상태가 되면 then()을 이용하여 처리 결과 값을 받고  
  실패 상태가 되면 실패한 이유(실패 처리의 결과 값)를 catch()로 받을 수 있다.  
  
  즉, then( ) 메서드는 호출한 Promise가 resolve()를 호출했을 때 반환값을 콜백함수로 받아주며, 이 때 새로운 Promise를 반환한다.  
  catch() 메서드는 호출한 Promise가 reject()를 호출했을 때 반환값을 콜백함수로 받아주며, 이 때 새로운 Promise를 반환한다.
	
  ``` javascript
		const  promise=new  Promise((resolve, reject)=>{
			//비동기 작업 처리
			resolve는 비동기 작업이 정상적일때 호출할 콜백함수
			reject는 비동기 작업이 정상적으로 처리되지 않을때 호출할 콜백함수이다
			정상/비정상 결과물 반환시 resolve(정상 결과물)
			비정상적인 경우 reject(에러)호출한다
		});
  ```
  인자로 콜백함수 전달 한다 즉 콜백함수의 결과를 반환하기로 약속하는 것이다  

  1. Promise 객체 생성자를 이용해서 변수에 담기
  ``` javascript
		const  promise = new  Promise((resolve, reject)=>{
			setTimeout(( )=>{
				 //네트웍에서 데이타 받아오기
				 const data = 'success';
				 if(data === 'success') resolve('데이타 불러오기 성공');
				 else reject('데이타 불러오기 실패');
			}, 2000);
		});
  ```

  2. **resolve()**함수로 전달한 값은 Promise객체의 **then()**으로  
  **reject()**함수로 전달한 값은 Promise객체의 **catch()**으로  받을 수 있다.
  ``` javascript
  promise.then( (result) => {
        console.log(result);
        return '다시 반환: '+result;
      })
      .then( (result) => console.log(result) )
      .catch( err => console.log(err) )
      .finally(() => console.log('항상 실행'));
  ```
  
  
