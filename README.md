# oneplus

## 引入Bootstrapvue插件
* npm引入
```npm
npm install vue bootstrap-vue bootstrap
```
* main.js需要引入
```javascript
//切记不能引入reset.css，否则字体会简称1rem，页面胖了好大一圈
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
Vue.use(BootstrapVue)
Vue.use(IconsPlugin)
```

## 各组件关键点
### HomeBanner
* button-hover添加阴影，从左往右
```css
//还是早上脑子快一点，不过官方应该不是这么做的，我看了半天源码没实现了
.banner-button{
    margin-top: 40px;
    font-size: 24px;
    display: inline-block;
    background: #eb0028;
    color: #fff;
    text-align: center;
    line-height: 50px;
    padding: 0 3rem;
    border-radius: 2px;
    position: relative;
    transform: translate(0%); //关键一步，没有这一步没有动画
    overflow: hidden;
    &:hover{
    &::before{
    content: "";
    display: block;
    position: absolute;
    top: -1px;
    left: -1px;
    width: 100%;
    height: 100%;
    display: block;
    z-index: -1;
    background: #b8001f;
    border-radius: 2px;
    animation: moveButton .25s ease forwards;
    }
@keyframes moveButton {
  0%{
    opacity: 0;
    transform: translateX(-100%);
  }
  100%{
    opacity: 1;
    transform: translateX(0);
  }
}    
```
* 解决图片滑动到一定位置加载，我的逻辑
>1、获取当前需要加载图片距离顶部高度并且除以2，也就是当图片到达距屏幕上一半后渲染出来
>2、把图片距离顶部的高放到一个数组，以及绑定class的Boolean值放到一个数组中
>3、通过mounted钩子在渲染页面后获取不同图片渲染需要的高度
>4、进行循环图片值，进行动态绑定class
>5、切记别忘记使用**set**方法，不然不能实时的渲染当前的页面
```javascript
data () {
    return {
      buttonTop: [],
      isByron: [false, false]
    }
  },
  methods: {
    getButtontop () {
      this.buttonTop[0] = Math.floor((this.$refs.offsetone.offsetTop) / 2)
      this.buttonTop[1] = Math.floor((this.$refs.offsettwo.offsetTop) / 2)
      console.log(this.buttonTop)
    },
    getScroll () {
      // console.log(document.documentElement.scrollTop)
      for (let i = 0; i < this.buttonTop.length; i++) {
        if (this.buttonTop[i] < document.documentElement.scrollTop) {
          // 切记要使用set，否则不会渲染到页面，使用this.isByron[i]=true是无效的
          this.$set(this.isByron, i, true)
        } else {
          this.$set(this.isByron, i, false)
        }
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.getScroll)
    this.getButtontop()
  }
```