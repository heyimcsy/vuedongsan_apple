<template>
  <div>
    <img :src="products.image" alt="image of room" class="room-img"/>
    <h4 @click="$emit('openModal',products.id)" >{{products.title}}</h4>
    <p> {{products.price}}</p>
  </div>
</template>
<script>
//props 는 read only
export default {
  name: 'cardComponent',
  props: {
    products: Object,
  }
}
</script>
<style>

</style>