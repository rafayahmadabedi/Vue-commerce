<template>
    <div id="page-wrap">
        <products-grid :products="products"></products-grid>
    </div>
</template>
<script>
import axios from "axios";
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
            await axios.get('/api/products')
            .then( res => this.products = res.data );
        }
    }
    
}
</script>
<style scoped>
    
</style>