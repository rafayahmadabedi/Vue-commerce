<template>
    
    <product-list-item v-for="product in cartItems" :key="product.id" :product="product"></product-list-item>
    
</template>
<script>
import ProductListItem from './ProductListItem.vue'
export default {
  components: { ProductListItem },
    name: "ProductsList",
    props: ["cartItems"]
}
</script>
<style scoped>

</style>