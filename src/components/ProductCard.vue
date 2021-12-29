<template>
  <div class="card">
    <div class="card-title">{{ product.name }}</div>
    <div class="card-body">
      <br>
      <img :src="product.img">
      <form>
        <div class="row">
          <div class="cell">
            <label>Xuất xứ:</label>
          </div>
          <div class="cell">
            <em>{{ product.type }}</em>
          </div>
        </div>
        <div class="row">
          <div class="cell">
            <label>Giá:</label>
          </div>
          <div class="cell">{{ product.price }}VNĐ</div>
        </div>
        <div class="row">
          <div class="cell">
            <label>Số lượng(kg):</label>
          </div>
          <div class="cell">
            <input type="number" v-model.number="quantity" />
          </div>
        </div>
      </form>
    </div>
    <div class="card-footer">
      <button @click="addToCart(product.name, quantity)" class="btn btn-light">
        Thêm vào giỏ hàng
      </button>
    </div>
  </div>
</template>
<script>
export default {
  props: ['product', 'index', 'addToCart'],
  data () {
    return {
      quantity: 0
    }
  }
}
</script>
