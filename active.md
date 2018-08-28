### 未完成
1. nav中的状态设置
    1. `mounted()` 声明周期，当页面有滚动事件时需要使用它，不然scroll事件不会一直触发。
1. slider
    1. 增加了`slide`中的css
    1. `<swiper :options="swiperOption">`冒号的理解
        1. 应该是综合`swiper`属性，属性方式和官网一样
    1. slot
        1. 插槽
        1. 作用：文档中默认的，应该是如果`options`里面有`pagination`这个属性就显示，没有就不显示。
    1. vuex
        1. 已经了解完毕
    1. [使用vue-awesome-swiper的注意点](https://www.jianshu.com/p/47b09b528423)
1. my
    1. [使用vue-infinite-scroll在vue中实现下拉加载数据，瀑布流，详细操作](https://segmentfault.com/a/1190000011693433)
        1. infinite-scroll-disabled="busy"为true，禁止无线滚动，false可以滚动
    1. [vue-lazyload懒加载](https://github.com/hilongjw/vue-lazyload)

1. vue加载本地图片，不能`path: './assets/logo.png'`必须`path: require('./assets/logo.png')`或者import

1. 映射数据 ...mapActions
    1. 将原先的这种样式`methods:mapActions(['increment'])` 修改为`methods:{...mapActions([])}`
