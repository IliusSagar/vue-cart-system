<template>
  <div class="product">
    <div class="product-image">
      <img :src="selectedProduct.thumbnail" alt="" />
    </div>
    <div class="product-details">
      <p>Brand: {{ selectedProduct.brand }}</p>
      <p>Description: {{ selectedProduct.description }}</p>
      <p>Price: {{ selectedProduct.price }}</p>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'ProductDetails'
})
</script>

<script setup>
import { productsStore } from '@/stores/products'
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const store = productsStore()
const route = useRoute()

const selectedProduct = computed(() => {
  return store.products.find((item) => item.id === Number(route.params.id))
})
</script>

<style scoped>
.product {
  display: flex;
  margin-top: 50px;
}

.product-image {
  margin-right: 24px;
}
</style>
