<template>
  <div  class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <img :src="products[push].image" />
      <h4>{{products[push].title}}</h4>
      <p>{{products[push].content}}</p>
    <input @input="month = $event.target.value">
      <!-- <input v-model="month"> -->
      <p>{{month}}개월 선택함:{{products[push].price*month}}</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>
<script>

export default {
  name: 'modalComponent',
  data(){
    return{
      month: 1,
    } 
  },
  watch: {
   month(a){
    console.log('a',a)
    if(a > 12){
      alert('13이상 입력하지 마세요')
      this.month = 1
    }
   }
  },
  beforeUpdate(){
   if(this.month == 2){
    alert('2개월은 너무 적어 안 팝니다.')
   }
  },
  props: {
    products: Array,
    push: Number,
    modal: Boolean,
  }
}

</script>
<style>

</style>