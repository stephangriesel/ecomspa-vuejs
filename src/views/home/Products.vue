<template>
  <div style="padding: 25px;">
    <div class="page-wrapper">
      <div class="item">
        <div v-for="product in products" :key="product.id">
          <ProductCard :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import {mapActions, mapGetters} from 'vuex';
import ProductCard from './ProductCard.vue';
export default {
  computed: {
    ...mapGetters('product', ['products']),
  },
  components: {ProductCard},
  methods: {
    ...mapActions('product', ['getProducts', 'addCart', 'removeCart']),
  },
  mounted() {
    this.getProducts();
  },
};
</script>
<style></style>
