<template>
  <div class="home">
    <ShoppingCart v-bind:cart="cart"/>
    <div id="app">
      <h1>
        <img class="logo" alt="Vue logo" src="../assets/logo.png">The Vue.js Shop
      </h1>
      <div id="nav">
        <router-link to="/">Home</router-link>
        <router-link to="/checkout">Checkout</router-link>
        <router-link to="/about">About</router-link>
      </div>
      <div v-if="loading">Loading</div>
      <ProductList v-if="!loading" v-bind:products="products" v-on:add-to-cart="addToCart"></ProductList>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Welcome from "@/components/Welcome.vue";
import ProductList from "@/components/ProductList.vue";
import ShoppingCart from "@/components/ShoppingCart.vue";

export default {
  name: "home",
  components: {
    ProductList,
    Welcome,
    ShoppingCart
  },
  created() {
    this.fetchData();
  },
  data() {
    return {
      loading: true,
      post: null,
      error: null,
      products: [],
      cart: window.cart || {
        total: 0,
        items: [],
        cost: 0
      }
    };
  },
  methods: {
    async fetchData() {
      const resp = await fetch("https://kev-pi.herokuapp.com/api/products");
      const products = await resp.json();
      this.cart = window.cart || {
        total: 0,
        items: [],
        cost: 0
      };
      this.products = products;
      this.loading = false;
    },
    addToCart(product) {
      console.log("add to cart", this.cart.items);
      if (this.cart.items.filter(i => i.id === product.id).length === 0) {
        this.cart.items.push({ ...product, quantity: 1 });
      } else {
        this.cart.items.filter(i => product.id === i.id)[0].quantity++;
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
