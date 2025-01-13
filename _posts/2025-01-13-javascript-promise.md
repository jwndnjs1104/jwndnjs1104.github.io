---
title: Javascript Promise 비동기함수
date: 2025-01-13 00:00:00 +09:00
categories: [Javascript, Promise]
tags:
  [
    Javascript,
    Promise,
    비동기함수수
  ]

---


## **<span style="color: steelblue; visibility: hidden;">Javascript Promise</span>**

### Promise란?
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



