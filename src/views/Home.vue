<template>
  <div class="home">
      <div class="splash-container">
        <div class="splash">
          <h1>TRẠI NÔNG SẢN</h1>
        </div>
      </div>
      <main class="wrapper">
        <h2>Sản phẩm mới thu hoạch</h2>
        <div class="recommended">
          <ProductCard
           v-for="(product, index) in inventory.slice(0,3)"
            :key="product.id"
            class="card"
            :index="index"
            :product="product"
            :addToCart="addToCart"
            >
          </ProductCard>
        </div>
      </main>
  </div>
</template>
<script>
import ProductCard from '../components/ProductCard.vue'
export default {
  name: 'Home',
  props: ['inventory', 'addToCart'],
  components: {
    ProductCard
  }
}
</script>
