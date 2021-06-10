<template>
  <banner/>

  <div class="black-bg" v-if="proView==true">
    <div class="white-bg">
      <img v-bind:src="product[proNum].image">
      <div>{{product[proNum].title}}</div>
      <div>{{product[proNum].price}}</div>
      <div>{{product[proNum].content}}</div>
      <button v-on:click="proView=false">닫기</button>
    </div>
  </div>
  
  <ul class="view">
    <li v-for="(item,i) in product" :key="i">
      <img v-bind:src="product[i].image">
      <div>{{product[i].title}}<span v-on:click="proView=true,proNum=i">[상세보기]</span></div>
      <div>{{product[i].price}}</div>
    </li>
  </ul>
  
</template>

<script>
import vdata from './data.js'
import banner from './components/banner.vue'

export default {
  name: 'App',
  data(){
    return{
      proView:false,
      product:vdata,
    }
  },
 components:{
  //  banner:banner, 키값이 같으면 한번만 가능
   banner
 }
  
}
</script>

<style>
  *{margin: 0;padding: 0;}
  li{list-style: none;}
  img {width: 100%;}
  .view li {margin-bottom: 20px;}
  
  .black-bg {position: fixed; width: 100%; height: 100%; background: rgba(0,0,0,0.3); display: flex; justify-content: center; align-items: center;}
  .white-bg {position: fixed; width: 300px; height: 400px; background: #fff; padding: 20px; border-radius: 10px;}
  .white-bg img {width: 100%; margin-top: 20px;}
</style>
