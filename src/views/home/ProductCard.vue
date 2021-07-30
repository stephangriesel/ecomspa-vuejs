<template>
  <div class="card">
    <img :src="product.imageUrl" class="product-image" />
    <div class="card-body">
      <h5 class="card-title">{{ product.name }}</h5>
      <div class="item">
        <router-link type="button" class="btn" :to="'/details/' + product.id"
          >Details</router-link
        >
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'ProductCard',
  props: ['product'],
};
</script>
<style>
.card .product-image {
  height: 300px;
}
</style>
