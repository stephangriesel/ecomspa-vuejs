<template>
  <div class="item">
    <div>
      <label for="inlineFormInputName2">Quantity</label>
      <input type="number" v-model="quantity" class="form-control" />
    </div>
    <button
      v-if="!isInCardProp"
      @click.stop="addCart({product, quantity})"
      type="button"
      class="btn"
    >
      ADD TO CART
    </button>
    <button
      v-else
      @click.stop="removeCart(product.id)"
      type="button"
      class="btn"
    >
      REMOVE FROM CART
    </button>
  </div>
</template>
<script>
import {mapActions, mapState} from 'vuex';
export default {
  props: ['product'],
  data() {
    return {
      isInCardProp: false,
      quantity: 1,
    };
  },
  computed: {
    ...mapState('product', ['cart']),
  },
  methods: {
    ...mapActions('product', ['addCart', 'removeCart']),
    isInCart(id) {
      for (let index = 0; index < this.cart.length; index++) {
        const element = this.cart[index];
        if (element.id === id) {
          return true;
        }
      }
      return false;
    },
  },
  watch: {
    product(val) {
      this.isInCardProp = this.isInCart(val.id);
    },
    cart() {
      this.isInCardProp = this.isInCart(this.product.id);
    },
    quantity(val) {
      if (val <= 0) {
        this.quantity = 1;
      }
    },
  },
};
</script>
<style></style>
