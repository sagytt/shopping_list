<template>
  <div class="hello">
    <ul>
      <li v-for="(product, i) in this.products">
        {{product.name}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ProductsList',
  props: {
    products: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}

a {
  color: #42b983;
}
</style>
