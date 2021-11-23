<template>
    <div class="grid-wrap">
        <product-grid-item v-for="product in products" :key="product.id" :product="product"></product-grid-item>
    </div>
</template>
<script>
import ProductGridItem from './ProductGridItem.vue'
export default {
    name: 'ProductsGrid',
    components: {
        ProductGridItem
    },
    props: ["products"]
    
}
</script>
<style scoped>
.grid-wrap {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin-top: 16px;
}
</style>