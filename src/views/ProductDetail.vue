<template>
    <div id="page-wrap" v-if="product.id">
        <div id="image-wrap">
            <img :src="product?.imageUrl" :alt="product?.name">
        </div>
        <div id="product-details">
            <h1>{{ product?.name }}</h1>
            <h3 id="price">${{ product?.price }}</h3>
            <p>Average Rating: {{ product.averageRating }}/5</p>

            <button id="add-to-cart" @click="addToCart">Add To Cart</button>

            <h4>Description</h4>
            <p>{{ product.description }}</p>
        </div>
    </div>
    <NotFound v-else />
</template>

<script>
import NotFound from '../views/NotFound.vue'
import axios from 'axios';

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
            await axios.get(`/api/products/${id}`)
            .then( res => this.product = res.data );
        },
        async addToCart () {
          await axios.post(`/api/users/12345/cart`, {
            productId: this.$route.params.id
          })
          .then( res => console.log('Added into the cart', res.data.length));

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
