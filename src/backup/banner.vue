<template>
  <div class="banner">
      {{text}}
  </div>
</template>

<script>
export default {
    name:'banner',
    data(){
        return{
            text:'자전거'
        }
    }
}
</script>

<style>
    .banner {
        width: 100%; height: 100px;
        background: #aaa;
        display: flex; justify-content: center;
    }
</style>