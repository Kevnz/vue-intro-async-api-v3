<template>
  <div class="cards">
    <div class="card" v-for="product in products" v-bind:key="product.id">
      <img class="product" v-bind:src="product.image" v-bind:alt="product.name">
      <h3>{{product.name}}</h3>
      <p>{{product.description}}</p>
      <a href="#" v-on:click="addToCart(product, $event)">
        {{product.price}}
        <font-awesome-icon icon="cart-plus" size="1x"/>
      </a>
    </div>
  </div>
</template>

<script>
import CartIcon from "./CartIcon.vue";
export default {
  props: ["products"],
  components: {
    CartIcon
  },
  methods: {
    addToCart: function(product, e) {
      e.preventDefault();
      this.$emit("add-to-cart", product);
    }
  }
};
</script>

<style scoped>
img.product {
  width: 180px;
  height: 130px;
}
p {
  min-height: 120px;
}
svg {
  vertical-align: top;
  stroke: white;
  width: 20px;
  height: 20px;
  margin-left: 10px;
}
</style>
