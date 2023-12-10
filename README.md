# 영화 추천 사이트 with Vue

## 개요

## 타겟

## 디자인 

## 사용할 API
movie API: https://developer.themoviedb.org/reference/intro/getting-started

## 사용 프레임워크
Vue의 핵심 기능과 개념은 다음과 같습니다:

컴포넌트 기반 아키텍처: Vue는 컴포넌트라는 작은 조각들로 애플리케이션을 구성합니다. 각 컴포넌트는 자체 상태와 뷰를 가지며, 재사용 가능하며 관리하기 쉽습니다.

반응형 데이터 바인딩: Vue는 데이터와 뷰를 양방향으로 연결할 수 있습니다. 데이터가 변경되면 자동으로 화면이 업데이트됩니다. 이를 통해 개발자는 복잡한 DOM 조작을 최소화하고 코드를 간단하게 유지할 수 있습니다.

디렉티브: Vue는 HTML 요소에 특별한 속성을 추가하여 동적으로 요소를 조작하도록 지원합니다. 예를 들어, v-for, v-if, v-bind, v-on과 같은 디렉티브를 사용하여 템플릿과 데이터 간의 상호 작용을 제어할 수 있습니다.

라우팅 및 상태 관리: Vue Router와 Vuex와 같은 공식 라이브러리를 사용하여 라우팅 및 상태 관리를 손쉽게 처리할 수 있습니다.

커뮤니티 및 에코시스템: Vue는 활발한 커뮤니티와 다양한 플러그인 및 라이브러리 생태계를 가지고 있어 개발자들이 다양한 기능을 확장하고 공유할 수 있습니다.



## git
echo "# movie-project" >> README.md
  git init
  git add README.md
  git commit -m "first commit"
  git branch -M main
  git remote add origin https://github.com/SeoEugene/movie-project.git
  git push -u origin main



  `git add .`
  `git commit -m "커밋 메시지"`
  `git push origin main`

### install
`create vue@latest`
√ Project name: ... .
√ Package name: ... movie
√ Add TypeScript? ... No / Yes
√ Add JSX Support? ... No / Yes
√ Add Vue Router for Single Page Application development? ... No / Yes  
√ Add Pinia for state management? ... No / Yes
√ Add Vitest for Unit Testing? ... No / Yes
√ Add an End-to-End Testing Solution? » No
√ Add ESLint for code quality? ... No / Yes
√ Add Prettier for code formatting? ... No / Yes
`npm install`
`npm run format`
`npm install sass`
`npm install axios`

### run
`npm run dev`

### build
`npm run build`


## Ppst man



### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

`git add . 명령어 오류`
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it
해결방법: `git pull origin master --allow-unrelated-histories`



`npm install -g create-vite`