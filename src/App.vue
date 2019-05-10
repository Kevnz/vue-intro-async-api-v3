<template>
  <div id="app" class="container">
    <router-view/>
    <github-corner/>
  </div>
</template>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav a {
  text-decoration: none;
  margin-left: 10px;
  margin-right: 10px;
  color: #2c3e50;
}
body {
  border-top: 0.6rem solid #42b983;
  padding: 0;
  margin: 0;
}
.container {
  border-top: 0.2rem solid #2c3e50;
}
h1 {
  font-size: 3rem;
  margin-top: 0;
  font-family: "Avenir Next", system-ui, sans-serif;
  font-weight: normal;
}
.logo {
  max-width: 100px;
  margin-right: 20px;
  vertical-align: middle;
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
.primary-btn {
  color: #fff;
  background: #42b983;
  padding: 4px;
  margin: 4px;
  border: #42b983 solid 1px;
  border-radius: 2px;
  font-size: 0.9rem;
}

.primary-btn:hover {
  color: #fff;
  background: #215c41;
}
</style>
