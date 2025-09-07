# <a href="https://tailwindcss.com/">Tailwind CSS</a>
유틸리티 우선의 CSS 프레임워크, html 직접 스타일 정의<br>
모듈화, 디자인 일관성 유지, 유연성<br>

#### When?
- 빠른 UI 프로토 제작
- 유지 보수 < 개발 속도

장점
- 빠른 스타일 작성 및 최소한의 CSS
- hover, focus 등 내장 지원

단점
- 클래스명이 길어짐
- 커스터마이징 복잡
- 스타일, 로직 분리 약해짐

<ul>
    <li>CSS 파일이 커질 수록 로딩이 느려짐</li>
</ul>

#### 설치 방법
v4부터 dist 폴더 생성

```
npm install -D tailwindcss@latest postcss autoprefixer // npm install tailwindcss @tailwindcss/cli

npx tailwindcss init -p가 안되니깐 tailwind.config.js, postcss.config.js를 만들어야 됨
===================================
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{js,jsx}"
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
===================================
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
===================================
근데 module is not defined 떠서 해결하려면 .eslintrc.js 파일을 수정해야 되는데 없음 그래서 설치 해야 됨
근데 eslint.config.js가 이미 있음 같이 쓰면 안 됨 개같은 경우를 봤나

// .eslintrc.js 파일 설치
npm install -D eslint

npx eslint --init
=======
√ What do you want to lint? · javascript
√ How would you like to use ESLint? · problems
√ What type of modules does your project use? · esm
√ Which framework does your project use? · react
√ Does your project use TypeScript? · no / yes
√ Where does your code run? · browser
The config that you've selected requires the following dependencies:

eslint, @eslint/js, globals, eslint-plugin-react
√ Would you like to install them now? · No / Yes
√ Which package manager do you want to use? · npm
=======
하다가 찾아 냈다
npm install -D tailwindcss@3.3.2 postcss@8 autoprefixer@10

npx tailwindcss init -p
드디어 된다

tailwind.config.js
================
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,jsx}", // React 컴포넌트 경로 포함
  ],
  theme: {
    extend: {},
  },
  plugins: [],
};
=======or=========
module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{js,jsx}", // React 컴포넌트 경로 포함
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
================

```
자동정렬

```
headwind

========================= 
npm install -D prettier-plugin-tailwindcss@latest
npm install -D prettier prettier-plugin-tailwindcss

// .vscode/settings.json 공통
{
  "editor.formatOnSave": true, // 파일을 저장할 때마다 포맷팅 실행
  "editor.defaultFormatter": "esbenp.prettier-vscode" // 기본 포맷터를 Prettier로 지정
}


// preittier.config.js
/** @type {import("prettier").Config} */
export default {
  // 플러그인을 여기에 등록합니다.
  plugins: ["prettier-plugin-tailwindcss"],
};
==========================
npm install -D prettier prettier-plugin-tailwindcss - 자동 정렬 잘 됨, 권장

// prettier.config.mjs
/** @type {import('prettier').Config & import('prettier-plugin-tailwindcss').PluginOptions} */
export default {
  plugins: ["prettier-plugin-tailwindcss"],
};




```
```
// 예시
<div className="w-12 h-10 text-white bg-gray-400"></div>
<div className="w-full h-10 bg-red-400 text-blue-200">text</div>
<div className="flex bg-slate-100 mt-3"></div>
```
