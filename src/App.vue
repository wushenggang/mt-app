<template>
  <div id="app">
    <!-- header-->
    <app-header :poiInfo="poiInfo"></app-header>
    <!-- nav -->
    <app-nav></app-nav>

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
      poiInfo:{}
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
  }
}
</script>

<style>
</style>
