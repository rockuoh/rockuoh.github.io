---
layout: post
title:  "[훑어보기] 리엑트 - Ref로 Dom 다루기"
categories: [프론트엔드, react]
tags: [react, javascript, frontend]
---

그려진 화면은 dom tree로 구성되어 있고 이를 조작하는 것이므로 “DOM을 조작한다”고 함

## useRef
예시로 "렌더링 직후에 특정 dom을 선택하거나 핸들링"하는데 활용됨. 기본적으로 아래 문법을 따름

```react
const someRef = React.useRef();
...
<>
    <div ref={someRef}> </div>
</>
```

useRef를 활용해서 기존 JS에서 특정 dom(또는 element)를 선택해서 조작하듯이 활용할 수 있음.
그렇다면 useRef는 왜 쓰는 걸까?
  - useState, useEffect와 같은 맥랙으로 react에서의 virtual dom, re-render 등을 활용하기 위해서 씀

## [활용예시]
```react
const App = () => {
  const inputRef = React.useRef();
  const divRef = React.useRef();

  React.useEffect(() => {
    inputRef.current.focus();
    setTimeout(() => {
      divRef.current.style.backgroundColor = "grey";
    }, 1500);
  }, []);
  return (
    <>
      <input ref={inputRef} />
      <div
        ref={divRef}
        style={ { height: 100, width: 200, backgroundColor: "black" } }
      />
    </>
  );
};
```
