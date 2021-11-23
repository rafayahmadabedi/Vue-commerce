<template>
    <div id="page-wrap">
        <h1>Shoppping Cart</h1>

        <div v-if="cartItems.length">
          <products-list :cartItems="cartItems"></products-list>

          <h3 class="total-price">Total: ${{ totalPrice }}</h3>
          <button id="checkout-button">Proceed To Checkout</button>
        </div>
        <p v-else>
          Your cart is empty, add items now!
        </p>
    </div>
</template>
<script>
import ProductsList from '../components/ProductsList.vue';
export default {
  components: { ProductsList },
    name: 'Cart',
    created() {
        this.getCartItems();
    },
    data() {
        return {
            cartItems: []
        }
    },
    methods: {
        async getCartItems() {
            await fetch('https://dummyjson.com/carts')
            .then(res => res.json())
            .then(cart => this.cartItems = cart.carts[0].products);
        }
    },
    computed: {
        totalPrice() {
            return this.cartItems.reduce(
                (sum, item) => sum + Number(item.price), 0
            );
        }
    }
}
</script>

<style scoped>
  h1 {
    border-bottom: 1px solid black;
    margin: 0;
    margin-top: 16px;
    padding: 16px;
  }

  #total-price {
    padding: 16px;
    text-align: right;
  }

  #checkout-button {
    width: 100%;
  }
</style>