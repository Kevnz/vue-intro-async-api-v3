<template>
  <div class="checkout">
    <ShoppingCart v-bind:cart="cart" />
      <div id="app">
        <img alt="Vue logo" src="@/assets/logo.png">
        <Welcome msg="The Vue.js Shop Checking Out"/>
        <CartList v-bind:cart="cart" v-on:remove-from-cart="removeFromCart"></CartList>
      </div>
  </div>
</template>

<script>

// @ is an alias to /src
import Welcome from "@/components/Welcome.vue";
import CartList from "@/components/CartList.vue";
import ShoppingCart from "@/components/ShoppingCart.vue";


export default {
  name: 'checkout',
  components: {
    CartList,
    Welcome,
    ShoppingCart
  },
  data() {
    console.log('win cart', window.cart)
    return {
      products: window.cart || [],
      cart: window.cart || [],
    };
  },
  methods: {
    removeFromCart(product) {
      console.log('Do not know?')
      const items = window.cart.items.filter(i => i.id !== product.id)
      window.cart.items = items
      this.cart = window.cart
    }
  }
}
</script>
