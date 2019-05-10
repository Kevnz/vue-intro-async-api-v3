<template>
  <div class="checkout">
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
      <CartList v-bind:cart="cart" v-on:remove-from-cart="removeFromCart"></CartList>

      <button class="primary-btn" id="show-modal" @click="showModal = true">Continue</button>
      <!-- use the modal component, pass in the prop -->
      <modal v-if="showModal" @close="showModal = false">
        <h3 slot="header">Vue Shop</h3>
        <div slot="body">
          <form class="checkout">
            <div class="checkout-header">
              <h4 class="checkout-title">
                Checkout
                <span class="checkout-price">${{cart.cost}}</span>
              </h4>
            </div>
            <p>
              <input
                type="text"
                class="checkout-input checkout-name"
                placeholder="Your name"
                autofocus
                required
              >
              <input type="text" class="checkout-input checkout-exp" placeholder="MM" required>
              <input type="text" class="checkout-input checkout-exp" placeholder="YY" required>
            </p>
            <p>
              <input
                type="text"
                class="checkout-input checkout-card"
                placeholder="4111 1111 1111 1111"
                required
              >
              <input type="text" class="checkout-input checkout-cvc" placeholder="CVC" required>
            </p>
            <p>
              <button
                type="button"
                class="primary-btn"
                @click="checkOut"
                :disabled="processing"
              >Purchase</button>
              <button class="checkout-btn-cancel" type="button" @click="showModal = false">Cancel</button>
            </p>
          </form>
        </div>
        <div slot="footer"></div>
      </modal>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Welcome from "@/components/Welcome.vue";
import CartList from "@/components/CartList.vue";
import ShoppingCart from "@/components/ShoppingCart.vue";
import Modal from "@/components/Modal.vue";
import { delay } from "@kev_nz/async-tools";

export default {
  name: "checkout",
  components: {
    CartList,
    Welcome,
    ShoppingCart,
    Modal
  },
  data() {
    console.log("win cart", window.cart);
    return {
      processing: false,
      showModal: false,
      products: window.cart || [],
      cart: window.cart || []
    };
  },
  methods: {
    async checkOut() {
      this.processing = true;
      console.info(this.cart);

      const response = await fetch(
        "https://kev-pi.herokuapp.com/api/long/wait",
        {
          method: "POST",
          mode: "cors",
          cache: "no-cache",
          credentials: "same-origin",
          headers: {
            "Content-Type": "application/json"
          },
          redirect: "follow",
          referrer: "no-referrer",
          body: JSON.stringify(this.cart)
        }
      );
      const { result, ...returnResult } = await response.json();

      console.info("returnResult", returnResult);
      this.processing = false;
      this.showModal = !result;
    },
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

<style scoped>
.checkout {
  text-align: left;
}

.checkout-name,
.checkout-card {
  width: 180px;
  margin-right: 10px;
}

.checkout-exp,
.checkout-cvc {
  width: 35px;
  margin-right: 5px;
}

.checkout-btn-cancel {
  color: #fff;
  background: #34495e;
  padding: 5px 15px;
  margin: 4px 4px 4px 0;
  border: #34495e solid 1px;
  border-radius: 2px;
  font-size: 0.9rem;
}
.checkout-btn-cancel:hover {
  background: #85919e;
}
</style>