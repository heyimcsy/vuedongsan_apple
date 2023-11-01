<template>
  <div class="discount">
    <h4>지금 결제하면 {{countdown}}% 할인</h4>
  </div>
</template>
<script >
export default {
  // name 은 항상 멀티 단어
  name: 'DiscountComponent',
  props: {
    countdown: Number,
  }
}

</script>
<style>

</style>

