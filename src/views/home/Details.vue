<template>
  <div class="page-wrapper">
    <div class="item">
      <div>
        <div class="card">
          <img :src="product.imageUrl" alt />
        </div>
      </div>
      <div>
        <div>{{ product.name }}</div>
        <p>{{ product.content }}</p>
        <div>
          <p>Price</p>
          <p>${{ product.price }}</p>
        </div>
        <AddToCart :product="product" v-if="user.uid" />
      </div>
    </div>
  </div>
</template>
<script>
import {mapGetters, mapActions} from 'vuex';
import AddToCart from '../../components/details/AddToCart';
export default {
  data() {
    return {
      isInCardProp: false,
    };
  },
  computed: {
    ...mapGetters('account', ['user']),
    ...mapGetters('product', ['product']),
  },
  components: {AddToCart},
  methods: {
    ...mapActions('product', ['productDetails']),
  },
  mounted() {
    this.productDetails(this.$route.params.idProduct);
  },
};
</script>
<style>
.container-fluid {
  padding: 30px;
}
.image-product {
  width: 100%;
}
.card * {
  max-height: 85vh;
}
</style>
