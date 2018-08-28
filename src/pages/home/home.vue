<template>
  <div class="home">
    <header-bar></header-bar>
    <nav-bar></nav-bar>
    <slider></slider>
    <hot-product :hotProducts="hotProducts"></hot-product>
    <hot-shop></hot-shop>
    <ul @click="cors">
      <h1>电影说明</h1>
      <li v-for="(item,index) in list" :key="index">
        <p>{{item.title}}&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{{ item.start_time }}</p>
        <a :href=item.uri>
          <img :src=item.cover alt="img">
        </a>
      </li>
    </ul>

  </div>
</template>

<script type="text/javascript">
  import {mapState, mapActions} from 'vuex'
  import HeaderBar from '../../components/header.vue'
  import NavBar from '../../components/nav.vue'
  import Slider from './slider.vue'
  import HotProduct from './hot_product.vue'
  import HotShop from './hot_shop.vue'

  import axios from 'axios'

  export default {
    data() {
      return {
        list: ''
      }
    },
    computed: {
      //映射State
      ...mapState([
        'hotProducts'
      ]),
    },
    mounted() {
      //获取热门商品列表
      this.getHotProducts();
      this.cors()
    },
    methods: {
      ...mapActions(['getHotProducts']),
      cors() {
        var that = this;
        axios('/rexxar/api/v2/muzzy/columns/10018/items?start=0&count=3')
          .then(function (response) {
            console.log(response);
            console.log(response.data.items);

            // that.list = response.data.items

            function get(data) {
              return data
            }

            let da = get({a: 123})
            // console.log(get(da));

          })
          .catch(function (error) {
            console.log(error);
          })
      }
      /*
      * 可以实现跨域问题，正确获取数据
      * 但是获取不到接口中的信息
      * */
    },
    components: {
      HeaderBar,
      NavBar,
      Slider,
      HotProduct,
      HotShop
    }
  }
</script>
<style lang="scss">
  @import '../../assets/css/home/products.scss';

  .home {
    padding-bottom: 30px;
    background-color: #f8f8fe;
  }

  .swiper-pagination .swiper-pagination-bullet {
    opacity: 1;
    background: #fff;
  }

  .swiper-pagination .swiper-pagination-bullet.swiper-pagination-bullet-active {
    background: #68cb78 !important;
  }
</style>
