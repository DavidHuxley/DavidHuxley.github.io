---
title: Typescript란 무엇일까?
date: 2023-06-23 23:17:00 +0900
categories: [Typescript]
tags: [Typescript]     # TAG names should always be lowercase
---

## Typescript? 

Typescript는 2012년에 Microsoft에 의해 개발된 오픈 소스 프로그래밍 언어로, Javascript에 Type을 부여한 언어이며 Javascript의 상위 집합언어다, 또한 Typescript는 Javascript에서 지원하지 않는 여러가지 강력한 기능을 제공하는데 다음과 같다.

* 엄격한 타입관리(Strongly Typed)
    - 컴파일 시점에 타입 검사
    - 스크립트 확장 시, 실시간 타입 검사 
* 제너릭(Generics)
    - 클래스, 함수가 사용될 때 타입 검사
* 인터페이스(Interface)
    - 타입 검사를 요구 

![](https://968663149-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-LDS-orWYJdO9Wve6CUx%2F-LDoRqknfjsiLCcr7LAK%2F-LDoRrpi3HqXZ5GeBzHG%2Ftypescript-compile.jpg?generation=1527740868432618&alt=media)

위의 그림과 같이 Typescript는 Javscript와 다르게 브라우저에서 바로 해석이 불가능하고 **Javascript로 변환해줘야 브라우저에서 정상적으로 사용가능**하다. 

Typescript가 Javascript로 출력되기에 컴파일러가 아닌 트렌스파일러(Transpiler)로 불리고 이러한 언어를 메타 언어(Meta Language)라고 부른다.

## Typescript를 사용하는 이유

Javascript보다 복잡하고 코드량도 더 많은데 어째서 대규모 프로젝트엔 반필수적으로 Typescript가 사용될까?

이는 직접 Typescript로 코드를 작성해보면 알게되는데 강력한 타입관리 기능 덕분에 실시간으로 디버깅이 가능하고, 코드의 가독성이 높아지며, 코드의 유지보수가 쉬워지기 때문이다. 특히 협업시에는 타입을 명시함으로써 코드의 의도를 명확히 알 수 있고, 타입을 명시함으로써 발생하는 버그를 줄일 수 있어 개발 생산성 향상에 큰 도움이 된다.

어떤식으로 에러가 발생하는지 간단한 예시를 통해 알아보자.

```javascript
// Javascript
function sum(a, b) {
    return a + b;
}

sum(10, '20'); // 1020
```

```typescript
// Typescript
function sum(a: number, b: number): number {
    return a + b;
}

sum(10, '20'); // error TS2345: Argument of type '"20"' is not assignable to parameter of type 'number'.
```

위의 예시를 보면 JS는 타입을 명시하지 않아도 암묵적 형변환(Implicit Coercion)때문에 sum 함수의 인자로 문자열을 넘겨도 에러가 발생하지 않는다. 하지만 TS는 타입을 미리 지정해뒀기 때문에 문자열을 넘겨주면 에러가 발생하고, 에러의 원인도 JS보다 명확하게 알려준다.

게다가 VSC에서 작업시 Typescript는 좀 더 최적화된 성능을 보여주는데 코드 작성 시 오탈자를 찾거나, auto-complete, auto-import 등의 편의성 기능이 기존의 JS보다 강화되었기 때문에 개발 생산성을 향상시키는데 큰 도움이 된다.

![](https://user-images.githubusercontent.com/8643457/125418761-c3f6503d-a9f7-442a-a28b-78665933f1e8.gif)

이후 포스팅엔 본격적으로 TS의 환경설정과 기본 문법, 여러가지 Type에 대해 알아보도록 하겠다.


