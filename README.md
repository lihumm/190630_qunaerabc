# qunarabc

> A Vue.js project

## Build Setup

``` bash
# 项目准备
1.码云上新建仓库qunaerabc
2.git clone 地址
3.npm install
4.npm run dev

#项目开发
1.构建项目结构
2.首页+城市页
3.引入reset.css初始化项目样式和fastclick.js处理移动端click事件300毫秒延迟
    (1)先执行安装fastclick的命令 npm install fastclick -S
    (2)之后在main.js中
        import FastClick from 'fastclick'
        FastClick.attach(document.body);
4.Vue中使用stylus
    npm install stylus stylus-loader --save
5.使用阿里图标iconfont
    (1)在官网上下载好图标,引入iconfont.css样式和.eot/.svg/.ttf/.woff后缀的字体文件
    (2)注意:iconfont.css文件如果和字体文件路径不同就需要修改iconfont.css文件的url路径引入部分

#首页开发步骤
1.轮播图使用vue-awesome-swiper插件 npm install vue-awesome-swiper@2.6.7 --save
2.icons部分也是用swiper插件,建议用float布局,这里用flex布局容易出问题
3.样式穿透(>>>) 如: .box >>> .swiper-pagination-bullet-active 这样就可以修改样式而不受scoped的限制了
4.hotList.vue部分添加样式overflow:auto --> 如果超出的内容被修剪，则浏览器会显示滚动条以便查看其余的内容
5.Like.vue的内容布局使用flex布局,右边设置flex:1和flex-direction: columns;
6.数据先是template里写然后改成在data中定义(注意:data中定义数据的imgUrl引入本地图片的话要require('@/asset/....jpg'))再最后使用mock模拟数据
7.使用mock模拟数据,使用步骤:
    (1)下载axios
        npm install axios --save
    (2)在组件中引用import axios from 'axios' 然后在方法中axios.get('/static/mock/index.json').then((res) =>{})
        由于/static/mock/这样引用不好,所以可以在config/index.js中配置代理,配置完就可以/api/index.js了,具体如下:
        proxyTable: {
        '/api':{
            target:'http://localhost:8080',
            pathRewrite:{
            '^/api':'/static/mock'
            }
      }
8.在Home.vue组件中有了ajax调用的数据,在组件名中绑定属性,子组件通过props接收

#城市页开发步骤
1.把页面高度还原出来
2.三个城市子模块给父元素添加ref="wrapper"绑定父元素,然后使用better-scroll插件
    npm install better --save
  在List.vue中引入import Bscrall from 'better-scroll'
  最后在script中写如下代码就可以实现滚动了 -->注意:父div先设置绝对定位写死不能滚动,其子div不要使用margin,不然使用better-scroll插件页面一进去就会滚动一下
    mounted() {
        this.scroll = new Bscroll(this.$refs.wrapper);
    },
3.点击右侧字母,调到相应城市,兄弟间的传值,子传父,父传子模式
  点击Alphabet.vue点击字母的时候使用$emit向外触发事件
    handleLetterClick(e){
        this.$emit('change',e.target.innerText)
    }
  然后父组件City.vue去监听这个事件
    handleLetterChange(letter){
        this.letter=letter
    }
  然后传递给另一个子组件<city-list :letter="letter"></city-list>
  List.vue这个子组件就props接收

4.Search.vue数据双向绑定keyword,根据输入的值和父组件传递过来的alphabetCity的值做比较,>-1就push进去
5.使用vuex数据共享城市页面和首页的城市
  步骤:(1)安装vuex插件 
        npm install vuex --save
       (2)新建store文件夹,方便管理,把stase和mutations部分单独抽取出来
       (3)兄弟之间传值需经过action和mutations,由于这里没有异步和批量处理,可以直接在mutations改值。Vuex 中的 mutation 非常类似于事件,有两个参数
       (4)state存数据,可以通过this.$store.state.city,可以使用辅助函数mapState,使用步骤
        导入 import { mapState } from 'vuex' 
        然后结合对象展开运算符...以使我们可以将最终对象传给 computed 属性,极大的简化我们代码
        computed: {
            //我把vuex里的city这个公用的数据,映射到我这个组件的conputed计算属性里,映射过来的名字叫做currentCity
            ...mapState({
                currentCity: "city"
            })
        },
        这样我们就可以直接this.city获取到city的值了
       (6)使用辅助函数mapMutations 可以直接获取到方法,如:
        this.$store.commit('changeClick',city)可以简写成this.changeClick(city)
       (7)Vuex 允许我们在 store 中定义“getter”（可以认为是 store 的计算属性）,mapGetters同上两个一样

#首页和城市页使用keep-alive优化
1.在App.vue中给router-vue的外层添加一层keep-alive，这样下次跳转到该路由就会从缓存中获取数据而不会重新发送请求
    <keep-alive>
      <router-view />
    </keep-alive>
2.使用keep-alive会多一个钩子函数activated()
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
