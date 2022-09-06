<template>
  <div class="container">
    <div class="cart">
      <h3>SEPET</h3>
      <ul>
        <li v-for="(item, index) in cartItems" :key="index">{{ item.title }}
          ({{item.count2}})
          <button @click="reduceProduct(index)">Eksilt</button>
          <button @click="deleteProduct(index)">Kaldir</button>
        </li>
      </ul>
      <p v-if="cartItems.length == 0">Sepetiniz bostur. Alisverise başlayabilirsiniz..</p>
    </div>
    <product @addToCart="addToCart" :product="product" v-for="product in productList" :key="product.id" />
  </div>
</template>

<script>
import productCom from "@/components/Product.vue";

export default {
  components: {
    'product': productCom
  },
  data() {
    return {
      count: 0,
      productList: [
        {
          id: 1,
          title: "MacBook Pro",
          price: 100,
          count: 0,
          description: "Aciklama 1"
        },
        {
          id: 2,
          title: "iPhone",
          price: 50,
          count: 100,
          description: "Aciklama 2"
        },
        {
          id: 3,
          title: "Klavye",
          price: 10,
          count: 1000,
          description: "Aciklama 3"
        }
      ],
      cartItems: [],
    }
  },
  methods: {
    addToCart(product) {
      if (this.cartItems.indexOf(product) != -1) {
        let index = this.cartItems.indexOf(product)
        this.cartItems[index]['count2']++
        this.cartItems.splice(0, 0)
      }
      else {
        product['count2'] = 1
        this.cartItems.push(product)
      }
    },
    reduceProduct(index) {
      // let index = this.cartItems.indexOf(product)
      this.cartItems[index]['count2']--
      this.cartItems.splice(0, 0)
    },
    deleteProduct(index) {
      // let index = this.cartItems.indexOf(product)
      this.cartItems.splice(index, 1)
    }
  }
}
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.cart {
  margin-bottom: 50px;
}
</style>


