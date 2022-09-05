<template>
  <div class="container">
    <div class="cart">
      <h3>SEPET</h3>
      <ul>
        <li v-for="item in cartItems" :key="item.id">{{item.title}}<p>Miktar: {{calculateCount}}
        </p></li>
      </ul>
      <p v-if="cartItems.length == 0">Sepetiniz bostur. Alisverise başlayabilirsiniz..</p>
    </div>
    <product @addToCart="cartItems.push($event)" :product="product" v-for="product in productList" :key="product.id"/>
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
      calculateCount() {
        count_product: count_product + 1
      }
    }
  }
}
</script>

<style>
  .container{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  },
  .cart{
    margin-bottom: 50px;
  }
</style>


