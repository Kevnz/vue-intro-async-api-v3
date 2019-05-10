<template>
  <div class="list">
    <div class="line-item" v-for="product in cart.items" v-bind:key="product.id">
      <p>
        <a href="#" v-on:click="removeFromCart(product, $event)">
          <img class="product" v-bind:src="product.image" v-bind:alt="product.name">
          {{product.name}} - {{product.quantity}}
          {{product.price}}
          <font-awesome-icon icon="minus-square" size="1x"/>
        </a>
      </p>
    </div>
  </div>
</template>

<script>
import CartIcon from "./CartIcon.vue";
import Modal from "./Modal.vue";

export default {
  props: ["products", "cart"],
  components: {
    CartIcon,
    Modal
  },
  data: {
    showModal: false
  },
  methods: {
    removeFromCart: function(product, e) {
      e.preventDefault();
      this.$emit("remove-from-cart", product);
    }
  }
};
</script>

<style scoped>
.list {
  padding-top: 20px;
  padding-left: 230px;
}
.line-item {
  text-align: left;
  margin-bottom: 10px;
}
.line-item:hover {
  background: #ccc;
}
img.product {
  width: 90px;
  height: 65px;
  display: inline-block;
  padding-right: 15px;
  vertical-align: middle;
}
p {
  min-height: 120px;
  display: inline;
}
svg {
  stroke: white;
  width: 20px;
  height: 20px;
  margin-left: 10px;
  vertical-align: middle;
  margin-top: -4px;
}
a {
  text-decoration: none;
  color: #2c3e50;
}
</style>
