<template>
  <transition name="fade">
    <Modal @closeModal="modal=false" :products="products" v-bind:push="push" :modal="modal"/>    
  </transition>

<div class="menu">
<a v-for="(menuName,i) in menu" :key="i">{{menuName}}</a>
</div>
<Discount :countdown="countdown"/>
<button @click="priceSort">가격순 정렬</button>
<button @click="priceRivertSort">가격역순 정렬</button>
<button @click="titleSort">이름순 정렬</button>
<button @click="sortBack">되돌리기</button>
  <Card
      @openModal="modal=true; push=$event"
      :products="products[i]"
      v-for="(product,i) in products"
      :key="product.id"/>
</template>
<script>
import roomList from './assets/oneroom'
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";
export default {
  name: 'App',
  data() {
    return{
      countdown: 20,
      showDiscount: true,
      productsOriginal: [...roomList],
      push: 0,
      modal:false,
      count: [0,0,0],
      menu:['Home','Shop','About'],
      style: "color: red",
      products:roomList
    }
  },
  methods : {
    priceSort(){
      var array= this.products.sort(
        function(a,b) {
          return a.price-b.price
        }
      )
      console.log('data',array)
    },
    priceRivertSort(){
    this.products.sort(
      function(a,b){
        return b.price -a.price
        }
      )
    },
    sortBack(){
      this.products = [...this.productsOriginal]
    },
    titleSort(){
this.products.sort(
  (a,b)=>a.title > b.title ? 1 : -1)
  },
  },
mounted(){
  
    setInterval(() => {
      if(this.countdown > 0){
    this.countdown = this.countdown -1;
      }
  }, 1000);    
  
},
  components: {
  Discount : Discount,
    Modal: Modal,
    Card: Card,
  }
}
</script>

<style>
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
transition: all 2s;
}
.fade-leave-to { 
opacity: 0;
}
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
transition: all 3s;
}
.fade-enter-to { 
opacity: 1;
}
body {
  margin :0
}
div {
  box-sizing: border-box;
}
.discount {
 background: #eee;
 padding: 10px;
 margin: 10px;
 border-radius: 5px; 
}
.black-bg {
  width: 100%; height:100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding:20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
