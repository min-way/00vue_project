<template>
  <banner/>

  <!-- <div class="black-bg" v-if="proView==true">
    <div class="white-bg">
      <img v-bind:src="product[proNum].image">
      <div>{{product[proNum].title}}</div>
      <div>{{product[proNum].price}}</div>
      <div>{{product[proNum].content}}</div>
      <button v-on:click="proView=false">닫기</button>
    </div>
  </div> -->
  
 <!-- <div class="start" v-bind:class="{end:proView}"> -->
   <transition name="show">
     <modal
     :product="product"
     :proView="proView"
     :proNum="proNum"
     @modalClose="proView=false"
     />
   </transition>
 <!-- </div> -->
  
  <!-- <ul class="view">
    <li v-for="(item,i) in product" :key="i">
      <img v-bind:src="product[i].image">
      <div>{{product[i].title}}<span v-on:click="proView=true,proNum=i">[상세보기]</span></div>
      <div>{{product[i].price}}</div>
    </li>
  </ul> -->
  <product 
  :product="product[i]" v-for="(item,i) in product" 
  :key="i" 
  @modalOpen="proView=true;proNum=$event" 
  />
</template>

<script>
import vdata from './data.js'
import banner from './components/banner.vue'
import modal from './components/modal.vue'
import product from './components/product.vue'

export default {
  name: 'App',
  data(){
    return{
      proNum:0,
      proView:false,
      product:vdata,
    }
  },
 
 components:{
  //  banner:banner, 키값이 같으면 한번만 가능
   banner,
   modal,
   product,
 }
  
}
</script>

<style>
  *{margin: 0;padding: 0;}
  li{list-style: none;}
  img {width: 100%;}
  .view li {margin-bottom: 20px;}
  .black-bg {position: fixed; top:0; left:0; width: 100%; height: 100%; background: rgba(0,0,0,0.3); display: flex; justify-content: center; align-items: center;}
  .white-bg {position: fixed; width: 300px; height: 400px; background: #fff; padding: 20px; border-radius: 10px;}
  .white-bg img {width: 100%; margin-top: 20px;}
  .start {opacity: 0; transition: 0.5s;}
  .start.end {opacity: 1;}

  .show-enter-from, .show-leave-to {opacity: 0; transform: translateY(1000px);}  
  .show-enter-active, .show-leave-active {transition: 0.5s;}  
  .show-enter-to, .show-leave-from {opacity: 1; transform: translateY(0);}

  /* .fade-enter-from {opacity: 0; transform: translateY(1000px);}  
  .fade-enter-active {transition: 0.5s;}  
  .fade-enter-to {opacity: 1; transform: translateY(0);} */

  /* .show-leave-from {opacity: 1;}
  .show-leave-active {transition: 0.3s;}
  .show-leave-to {opacity: 0;} */

</style>
