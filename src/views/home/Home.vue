<template>
  <div id="home">
    <nav-bar class="nav-bar"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners">
  </div>
</template>

<script>
  import NavBar from 'components/common/navbar/NavBar'
  import HomeSwiper from './childComps/HomeSwiper'
  import {getHomeMultidata} from 'network/home'
  export default {
    name:'Home',
    components:{
      NavBar,
      HomeSwiper
    },
    data(){
      return{
        banners:[],
        recommends:[]
      }
    },
    created(){
      this.getHomeMultidata().then(res => {
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list
      })
    }
  }
</script>

<style scoped>
  #home{
    height: 100vh;
  }
  .nav-bar{
    background-color: var(--color-tint);
    font-weight:700;
    color: white;
  }
</style>