<template>
    <div id="page-wrap" v-if="product.id">
        <div id="image-wrap">
            <img :src="product?.images[0]" :alt="product?.title">
        </div>
        <div id="product-details">
            <h1>{{ product?.title }}</h1>
            <h3 id="price">${{ product?.price }}</h3>
            <p>Average Rating: {{ product.rating }}/5</p>

            <button id="add-to-cart">Add To Cart</button>

            <h4>Description</h4>
            <p>{{ product.description }}</p>
        </div>
    </div>
    <NotFound v-else />
</template>

<script>
import NotFound from '../views/NotFound.vue'

export default {
    name: 'ProductDetail',
    components: {
      NotFound
    },
    created() {
        this.getProduct(this.$route.params.id);
    },
    data() {
        return {
            product: {}
        }
    },
    methods: {
        async getProduct(id) {
            await fetch(`https://dummyjson.com/products/${id}`)
            .then(res => res.json())
            .then( product => this.product = product );
        }
    }
}
</script>

<style scoped>
  #page-wrap {
    margin-top: 16px;
    padding: 16px;
    max-width: 600px;
  }

  #img-wrap {
    text-align: center;
  }

  img {
    width: 400px;
  }

  #product-details {
    padding: 16px;
    position: relative;
  }

  #add-to-cart {
    width: 100%;
  }

  #price {
    position: absolute;
    top: 24px;
    right: 16px;
  }
</style>