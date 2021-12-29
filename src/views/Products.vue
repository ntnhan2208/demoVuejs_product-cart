<template>
  <main class="wrapper">
    <h1>Tất cả sản phẩm</h1>
    <div class="card-container">
      <ProductCard
        v-for="(product, index) in inventory.slice(0, 12)"
        :key="product.id"
        class="card"
        :index="index"
        :product="product"
        :addToCart="addToCart"
      >
      </ProductCard>
    </div>
  </main>
</template>
<script>
import ProductCard from '../components/ProductCard.vue'
export default {
  props: ['inventory', 'addToCart'],
  components: {
    ProductCard
  }
}
</script>
