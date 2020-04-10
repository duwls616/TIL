# React

## React는 무엇인가
컴포넌트 기반 프론트엔드 라이브러리이다.  
Virtual DOM을 이용해 손쉽게 DOM을 이용하고 상태값을 관리한다.  
--> model의 변경이 있으면 뷰를 새로 그리자

## Virtual DOM
: 가상의DOM   
model에 변화가 있으면 javascript 상의 가상 DOM에 올려두고  
기존의 DOM과 비교하여 DOM 구조를 변경한다  
Vue, Marko, Maquette, Mithril...등이 사용한다.  

## 사용하기에 앞서 참고..
1. Webpack        
파일을 관리해주는 도구로써 의존하는 순서에 따라 파일을 생성해준다.   
확장자에 따라 번들링  
합쳐서 하나로 만들어주거나 분리해주거나  

2. Babel        
: javascript 도구  
script 신규 문법을 모든 브라우저가 제공하지 않는다.  
해당 오류를 줄이기위해 이전 스크립트 문법으로 변환해준다.  
 