<template>
 <banner/>

 <transition name="show">
    <modal 
    :product="product"
    :proView="proView"
    :proNum="proNum"
    @modalClose="proView=false"
    />
 </transition>


 <product 
 :product="product[i]" 
 v-for="(item,i) in product" :key="i" 
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
