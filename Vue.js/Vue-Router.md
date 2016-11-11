
## Vue-Router

### 라우터는 HTML, JS으로 선언 가능하다 

```html
  <div id="app">
  <h1>Hello App!</h1>
  <p>
    <!-- 네비게이션 바를 생성할 때 사용함-->
    <!-- to = 누르면 아래의 주소로 감 = 파싱될 때 <a> 태그로 바뀜-->
    <router-link to="/foo">Go to Foo</router-link>
    <router-link to="/bar">Go to Bar</router-link>
  </p>
  <!-- route outlet -->
  <!-- 컴포넌트가 여기에 매치될 것임
   -->
  <router-view></router-view>
</div>
```

```javascript
// 모듈 시스템을 쓰면 Vue.use(VueRouter) 해야함 

// 라우터 안에 들어갈 내용 정의 다른 파일에서 가져올 수도 있음 
const Foo = { template: '<div>foo</div>' }
const Bar = { template: '<div>bar</div>' }
// 2. 라우터
// 각각 라우터는 컴포넌트와 매치가 되야함 
// 뷰객체를 상속 받았든, 컴포넌트이든 상관 없음 
const routes = [
  { path: '/foo', component: Foo },
  { path: '/bar', component: Bar }
]

// 3. 라우터를 입력해줘야 라우터가 동작함
// 여기에서 다양한 컴포넌트를 만들어줄 수 있음
const router = new VueRouter({
  routes // short for routes: routes
})

// 4. 루트에 연결해줌 
const app = new Vue({
  router
}).$mount('#app')

```

### 동적 라우터 매칭
* 라우터 매칭을 함 
* 예를 들면 유저별로 보여지는 화면이 다를 때, vue-router는 동적으로 매치가 가능함
* 결국 라우터의 파라미터를 받아서 user 컴포넌트 내용을 동적으로 만든다라는 이야기 
* 사용할 수 있는 것 
  * $router.prams 
  * $router.query (=?~ URL에 쿼리스트링이 있다면)
  * $router.hash

## 파람 변화(=url의 동적인 부분)에 변경 부분에 대하여
* 다시 그리지 않고 캐시 해놓은 것이 나을 수 있음 
* 하지만 이건 라이프사이클의 훅이 호출되지 않을 수 있음 
* 정규식으로 패턴 매칭도 가능함 
* 먼저 선언된 것 라우터가 우선순위를 가짐 

### 라우터 안의 라우터 
* `<router-view>` 로 해당 컴포넌트를 넣을 수 있음 
* 라우터가 중첩되어 있으면 /를 루트로 간주함 
* 그래서 직접적으로 full url을 넣지 않고도 full url인 것 처럼 할 수 있음 
* 라우터의 children옵션은 또 다른 라우터를 생성하는 것과 같음 
* 니가 필요한 만큼 만들 수 있음
* 따로 지정하지 않았다면, 변경이 없을 것이지만 
* 서브 루트가 없을 경우 무엇인가 다른 액션을 보이고 싶으면 path:""를 넣어줌 
* 라우터의 컴포넌트 옵션에 객체로 지정하면 `<router-view>` 태그에 name 옵션을 넣을 수 있음 + 클래스랑 같이 쓸 때 유용한 건가?





