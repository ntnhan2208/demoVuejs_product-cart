<template>
<aside class="cart-container">
    <div class="cart">
      <h1 class="cart-title spread">
        <span>
          Giỏ hàng
          <i class="icofont-cart-alt icofont-1x"></i>
        </span>
        <button @click="toggle" class="cart-close">&times;</button>
      </h1>
      <div class="cart-body">
        <table class="cart-table">
          <thead>
            <tr>
              <th class="center">Sản phẩm</th>
              <th class="center">Giá(VNĐ)</th>
              <th class="center">SL(kg)</th>
              <th class="center">Tổng giá(VNĐ)</th>
              <th class="center"><span class="sr-only">Actions</span></th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(quantity,key,i) in cart" :key="i">
              <td class="center">{{key}}</td>
              <td class="center">{{getPrice(key)}}</td>
              <td class="center">{{quantity}}</td>
              <td class="center">{{(quantity*getPrice(key))}}</td>
              <td class="center">
                <button @click="remove(key)" class="btn btn-light cart-remove">
                  &times;
                </button>
              </td>
            </tr>
          </tbody>
        </table>
        <p class="center" v-if="!Object.keys(cart).length"><em>Chưa có sản phẩm nào trong giỏ hàng!</em></p>
        <div class="spread">
          <span><strong>Tổng cộng: </strong>{{calTotal()}} VNĐ</span>
          <button class="btn btn-light">Thanh toán</button>
        </div>
      </div>
    </div>
  </aside>
</template>
<script>
export default {
  props: ['toggle', 'cart', 'inventory', 'remove'],
  methods: {
    getPrice (name) {
      const product = this.inventory.find((p) => {
        return p.name === name
      })
      return product.price
    },
    calTotal () {
      const total = Object.entries(this.cart).reduce((acc, curr, index) => {
        return acc + (curr[1] * this.getPrice(curr[0]))
      }, 0)
      return total
    }
  }
}
</script>
