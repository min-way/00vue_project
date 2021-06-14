<template>
    <div>
      <img v-bind:src="product.image">
      <div>{{product.title}}</div>
        <span @click="$emit('modalOpen',product.id)">[상세보기]</span>
      <div>{{product.price}}</div>
    </div>
</template>

<script>
export default {
    name:'product',
    props:['product']
}
</script>

<style>

</style>