<template>
  <div class="list">
    <div class="card" v-for="product in cart.items" v-bind:key="product.id">
      <img class="product" v-bind:src="product.image" v-bind:alt="product.name" />
      <h3>{{product.name}}</h3>
      <p>{{product.description}}</p>
      <a href="#" v-on:click="removeFromCart(product, $event)">
        {{product.price}}
        <cart-icon />
      </a>
    </div>
  </div>
</template>

<script>
  import CartIcon from './CartIcon.vue'
  export default {
    props: ['products', 'cart'],
    components: {
      CartIcon
    },
    methods: {
      removeFromCart:function (product, e) {
        e.preventDefault()
        this.$emit('remove-from-cart', product);
      }
    }
  }
</script>

<style scoped>
  img.product {
    width:180px;
    height: 130px;
  }
  p {
    min-height: 120px;
  }
</style>
