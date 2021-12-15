<template>
    
    <product-list-item v-for="product in cartItems" :key="product.id" :product="product" @removeFromCart="removeCartItem"></product-list-item>
    
</template>
<script>
import axios from 'axios'
import ProductListItem from './ProductListItem.vue'
export default {
  components: { ProductListItem },
    name: "ProductsList",
    props: ["cartItems"],
    methods: {
      async removeCartItem(cartItem) {
        await axios.delete(`/api/users/12345/cart/${cartItem.id}`)

      }
    }
}
</script>
<style scoped>

</style>