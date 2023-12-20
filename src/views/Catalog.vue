<template>
  <div class="products-list">
    <div class="product" v-for="product in store.products" :key="product.id">
      <img :src="product.thumbnail" alt="" />
      <h2>Brand: {{ product.brand }}</h2>
      <h2>Description: {{ product.description }}</h2>
      <h2>Price: ${{ product.price }}</h2>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'CatalogView'
})
</script>

<script setup>
import { onMounted } from 'vue'
import { productsStore } from '../stores/products'

const store = productsStore()

onMounted(async () => {
  store.fetchProductsFromDB()

  console.log('Mounted >>>>>>>', store.products)
})
</script>

<style scoped>
.products-list {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.product {
  flex-basis: 28%;
  margin: 8px;
  padding: 16px;
  box-shadow: 0px 0px 14px 1px #e6e6e6;
  cursor: pointer;
}

.product img {
  width: 70%;
}
</style>
