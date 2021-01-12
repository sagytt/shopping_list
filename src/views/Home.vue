<template>
  <div class="home">
    <ul>
      <li
              v-for="(product, i) in this.products"
              :key="i"
              @click="selectProduct(i)">
        {{product.name}}, {{product.price}}, {{product.description}}
      </li>
    </ul>

    <EditProduct :product="this.selectedProduct" />
  </div>
</template>

<script>
// @ is an alias to /src
import ProductsList from '@/components/ProductsList.vue'
import EditProduct from '@/components/EditProduct.vue'

export default {
  name: 'Home',
  data() {
    return {
      products: [
        {
          name: 'Bread',
          price: 5,
          description: 'White bread'
        },
        {
          name: 'Milk',
          price: 4,
          description: '3% fresh milk'
        }
      ],
      selectedProduct: null
    }
  },
  methods: {
    selectProduct: function(i) {
      this.selectedProduct = this.products[i];
    }
  },
  components: {
    ProductsList,
    EditProduct
  }
}
</script>
