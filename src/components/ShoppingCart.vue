<template>
  <div>
    <cart-icon /> {{cart.total}}
  </div>
</template>

<script>
  import CartIcon from './CartIcon.vue'
  export default {
    props: ['cart'],
    components: {
      CartIcon
    },
    methods: {

    }
  }
</script>

<style scoped>
  div {
    font-size: .9rem;
    text-align: right;
    margin-top: 10px;
    margin-right: 25px;
  }
</style>
