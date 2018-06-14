<template>
  <div id="app">
    <!-- header-->
    <app-header :poiInfo="poiInfo"></app-header>
    <!-- nav -->
    <app-nav :commentNum="commentNum"></app-nav>

    <!-- content -->
    <router-view></router-view>
  </div>
</template>

<script>
  import Header from './components/header/Header'
  import Nav from './components/nav/Nav'
export default {
  name: 'App',
  components:{
    "app-header":Header,
    "app-nav":Nav
  },
  data(){
    return{
      poiInfo:{},
      commentNum:0
    }
  },
  created(){
    //axios


    //fetch
    fetch("/api/goods")
      .then(res=>{
        return res.json()
      })
      .then(response=>{
        if(response.code==0){
          this.poiInfo=response.data.poi_info;
        }
      })

    fetch("/api/ratings")
      .then(res=>{
        return res.json()
      })
      .then(response=>{
        if(response.code==0){
          this.commentNum=response.data.comment_num
        }
      })
  }
}
</script>

<style>
</style>
