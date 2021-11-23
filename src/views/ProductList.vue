<template>
    <div id="page-wrap">
        <products-grid :products="products"></products-grid>
    </div>
</template>
<script>
import ProductsGrid from '../components/ProductsGrid.vue';
export default {
    components: { ProductsGrid },
    name: 'ProductList',
    created() {
        this.getProducts();
    },
    data() {
        return {
            products: []
        }
    },
    methods: {
        async getProducts() {
            await fetch('https://dummyjson.com/products')
            .then( res => res.json())
            .then( products => this.products = products.products );
        }
    }
    
}
</script>
<style scoped>
    
</style>