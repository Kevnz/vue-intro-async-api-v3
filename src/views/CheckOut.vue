<template>
  <div class="checkout">
    <ShoppingCart v-bind:cart="cart"/>
    <div id="app">
      <h1>
        <img class="logo" alt="Vue logo" src="../assets/logo.png">The Vue.js Shop
      </h1>
      <div id="nav">
        <router-link to="/">Home</router-link>|
        <router-link to="/checkout">Checkout</router-link>|
        <router-link to="/about">About</router-link>
      </div>
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
  name: "checkout",
  components: {
    CartList,
    Welcome,
    ShoppingCart
  },
  data() {
    console.log("win cart", window.cart);
    return {
      products: window.cart || [],
      cart: window.cart || []
    };
  },
  methods: {
    removeFromCart(product) {
      const items = this.cart.items.filter(i => i.id !== product.id);
      const item = this.cart.items.filter(i => product.id === i.id);

      if (item.length > 0 && item[0].quantity > 1) {
        item[0].quantity--;
      } else if (item.length > 0 && item[0].quantity === 1) {
        this.cart.items = this.cart.items.filter(i => product.id !== i.id);
      }
      const q = this.cart.items.reduce((quantity, entry) => {
        return quantity + entry.quantity;
      }, 0);
      const cost = this.cart.items.reduce((amount, entry) => {
        return amount + entry.quantity * entry.price;
      }, 0);
      this.cart.total = q;
      this.cart.cost = cost;

      if (!window.cart) window.cart = {};
      window.cart = this.cart;
    }
  }
};
</script>
