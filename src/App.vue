<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/checkout">Checkout</router-link> |
      <router-link to="/cart">Cart</router-link> |
      <router-link to="/">About</router-link>
    </div>
    <router-view/>
  </div>
</template>



<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  border-top: 0.6rem solid #42b983;
  padding: 0;
  margin: 0;
}

.cards {
  display: flex;
  flex-wrap: wrap;
  align-items: stretch;
}

.card {
  flex: 0 0 180px;
  margin: 30px;
  border: 1px solid #ccc;
  box-shadow: 2px 2px 6px 0px rgba(0, 0, 0, 0.3);
  position: relative;
}

.card img.product {
  max-width: 100%;
  min-width: 100%;
}

.card .text {
  padding: 0 20px 20px;
}

.card a {
  background: gray;
  border: 0;
  color: white;
  padding: 10px;
  display: block;
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
}
</style>
