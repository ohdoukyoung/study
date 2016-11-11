# webpack + eslint  
* eslintrc 파일은 추가 되어있다고 가정함
* `yarn add eslint --dev` //eslint cli 사용불
* webpack을 사용한다면 추가적으로 eslint-loader를 추가 해야함
* `yarn add eslint-loader --dev`
```javascript
module: {
  preLoaders: [
    {
      test: /\.js$/,
      exclude: /node_modules/,
      loader: 'eslint' // eslint-loader로도 설정가능함 
    }
  ]
},
eslint: { //여기에서 여러가지  eslint 설정을 추가함 
    configfile : "eslintrc.js",
    failOnwaring: false
}

```

# eslint + babel
* import쓰고 싶으면(=ES6) 바벨로 컴파일 해주어야
```javascript
modeul:{
    loaders:[
        test:\/.js$/,
        exclude:/node_modules/,
        loaders:[babel-loader,...] //loaders가 되면 배열로 선언해야함 
    ]
}
```
# babel-eslint 는 ES6 코드를 린트해줌 
* `yarn add babel-eslint ---dev` 
* `.eslintrc` 에 `parser:"babel-eslint"` 옵션 추가함
* eslint에 설정에 맞는 플러그인이 있음 
* 확인하고 의존관계에 맞게 설치해야함 
* 여러가지 플러그인을 사용하면 eslint 옵션을 적용할 수 있음
    * [Example] `yarn add eslint-config-airbnb eslint-plugin-import-eslilnt-plugin-jsx-ally`
    * Vue에서 권장하는 플러그인은 ?
        - eslint-config-standard 
        - eslint-plugin-html //아마 템플릿때문에...?
        - eslint-plugin-promise
        - eslint-plubin-standard
* `extends : "standard"` 옵션을 넣어주면 각각의 config를 사용할 수 있음 각각 플러그인에서 정의하는 옵션을 넣어줌
* 
