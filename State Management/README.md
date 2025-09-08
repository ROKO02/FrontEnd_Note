# 상태 관리란?
애플리케이션 데이터를 효율적으로 관리

# Local State Management

## useState, useRef, useReducer
간단한 기능은 useState, 객체가 포함되어 복잡할 때는 useReducer<br>
useRef는 DOM 접근으로 비렌더링 상태 관리(자동 포커스, 이전 값 저장)<br>
 ==> 기본적으로 useState, 복잡하면 useReducer, 비렌더링 상태 useRef<br>
 컴포넌트 내부에서 관리 -> 불필요한 랜더링 방지 - 소규모 애플리케이션<br>
 단점 : prop drilling - 규모가 커지면 하위 컴포넌트로 prop 전달이 많아짐
 
```js
#useState
const [vlaue, setValue] = useState(m0);

setInputList([...inputList, inputValue]);

#useRef
const idRef = useRef(0);

#useReudcer
function reducer(state, action){
 switch(action.type)(
  case:
   return
  case:
   return
  defalut:
   return
 )
}

const [state, dispatch] = useReducer(reducer, 상태값)
#useReducer - distpatch
distpatch({
 type: "",
 data: "",
});
```

# Global State Management(전역 상태 관리)
## ✅ <a href="https://react.dev/learn/scaling-up-with-reducer-and-context">Context API</a>
prop을 사용하지 않고 데이터 공유(전역)<br>
단점 : 규모가 커지면 Context 또한 많아져 관리 어려움<br>
#### 사용 예시
- 테마/사용자/언어(지역) 데이터

```
const ValueContext = createContext();
```
 
## <a href="https://ko.redux.js.org/introduction/getting-started">Redux</a>
주요 개념
- Store : 상태 보관
- Action : 이벤트 설명 객체
- Reducer : 액션에 따라 상태 변경 함수
- Dispatch : 스토어에 전달

```
npm install redux
npm install react-redux
```

 when?
 - 대용량 상태 관리
 - 상태 업데이트가 빈번할 때

FLux 아키텍처 사용으로 단방향 데이터 흐름 -> 데이터 변화 예측 쉬움
- Flux 아키텍처 : 액션 -> 디스패쳐 -> 스토어 -> 뷰, 한 방향으로 데이터가 흘러감

javascript 전역 개발 라이브러리로 Vanilla JS, Angular, Vue 등 사용 가능<br>
단점 : 초기 설정 복잡함
 
### Redux-toolkit(RTK)
 <p>Redux를 간단하게 만드는 API 제공</p>

```
npm install @reduxjs/toolkit react-redux
```

## <a href="https://recoiljs.org/ko/">Recoil</a>
Facebook에서 개발한 React 전용 전역 상태 관리 라이브러리, Atomic(원자) 단위로 상태 관리 -> 유연하고 재사용성 높음
- Atoms : 상태 최소 단위, 업데이트, 구독 가능
- Selectors : 파생 상태 계산 함수, atoms or selector 입력 받아 파생 값 반환
  - ▶ 비동기 상태 관리가 쉽고 선택적 상태 구독을 통해 성능 최적화 가능
  - Next.js와 많이 사용됨
  - 
```
npm install recoil
```
 
## ✅ <a href="https://zustand-demo.pmnd.rs/">Zustand</a>
작은 크기와 단순한 함수 기반 API 제공하는 전역 상태 관리 라이브러리<br>
최소한의 리랜더링과 최적화 제공

```
npm install zustand
```

```js
// zustand는 모듈화를 통해서 전역 상태 관리를 할 수 있음
// useGuideStore.js
import { create } from "zustand";

const useGuideStore = create((set) => ({
  guideImg: null,
  guideText: null,
  setGuide: ({ guideImg, guideText }) => set({ guideImg, guideText }),
}));

export default useGuideStore;

// app.js
function App() {
  const guideImg = useGuideStore((state) => state.guideImg));
  const guideText = useGuideStore((state) => state.guideText));
  const setGuide = useGuideStore((state) => state.setGuide));

  return (
    <>
      <div className="card">
        <div{guideImg}</div>
        <div{guideText}</div>
      </div>
    </>
  );
}

export default App;
```

 <h1>Server State Management</h1>
 
 <h2>React Query</h2>

