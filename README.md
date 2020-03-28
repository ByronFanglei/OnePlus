# oneplus

## 引入Bootstrapvue插件
* npm引入
```npm
npm install vue bootstrap-vue bootstrap
```
* main.js需要引入
```js
//切记不能引入reset.css，否则字体会简称1rem，页面胖了好大一圈
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
Vue.use(BootstrapVue)
Vue.use(IconsPlugin)
```