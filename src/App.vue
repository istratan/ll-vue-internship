<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ProductList></ProductList>
  </div>
</template>

<script>

import ProductList from './components/product-list.component'

export default {
  name: 'App',
  components: {
    ProductList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.products-container {
  display: grid;
  grid-gap: 1rem;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  }

  .product-image{
    max-width: 230px;
  }

  .product-card {
    border: 1px solid black;
    display: flex;
    flex-direction: column;
    padding: 1rem;
  }

</style>
