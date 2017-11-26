---
layout: post
title: Using jquery in Rails
---
# Using jquery in Rails

rails에서 jquery를 사용하는 방법

일단 rails에서는 기본적으로 (5.0.버전 제외) jquery를 포함

### application.js 구조

```javascript
//= require jquery
//= require jquery_ujs
//= require turbolinks
//= require_tree .
```

기본적으로 포함되어 있는 부분
주의해야 할 점은 추가적으로 부트스트랩이나 다른 여타 js 라이브러리 gem을 설치할 때 항상 **jquery_ujs** 밑에 설치해야함

turbolinks의 역활은 header를 다시 안 불러오게 하기 위해서

tree .는 javascripts 폴더 안에 있는 내용들을 자동으로 불러오게 하기 위해서

### js 코드 작성(jquery 사용)

일반적으로 /app/assets/javascripts 폴더 안에 jquery메소드들이 실행 되지 않는 경우를 발견했다.

이거를 해결하는 방법은 [using-jquery-in-rails-part-i](http://yehudakatz.com/2007/01/31/using-jquery-in-rails-part-i/)

여기서 찾았는데 가장 간단히

```javascript
jQuery(function() {  
  // commands go here
})
```

이렇게 코드를 감싸고 해결하면 되었다.
