<template>
  <div class="about">
    <ShoppingCart v-bind:cart="cart"/>
    <div id="app">
      <h1>
        <img class="logo" alt="Vue logo" src="../assets/logo.png">The Vue.js Shop
      </h1>
      <div id="nav">
        <router-link to="/">Home</router-link>|
        <router-link to="/checkout">Checkout</router-link>|
        <router-link to="/cart">Cart</router-link>|
        <router-link to="/about">About</router-link>
      </div>
      <div>This is an example application used to demonstrate using Vue.js</div>
    </div>
  </div>
</template>
<script>
import ShoppingCart from "@/components/ShoppingCart.vue";

export default {
  name: "about",
  components: {
    ShoppingCart
  },
  data() {
    return {
      products: window.cart || [],
      cart: window.cart || []
    };
  }
};
</script>