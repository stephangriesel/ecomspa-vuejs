<template>
  <div>
    <div>
      <nav class="navbar">
        <router-link class="logo" to="/">VueShop</router-link>
        <div>
          <div v-if="user.photoURL">
            <img :src="user.photoURL" class="" alt />
            <router-link class="btn" to="/cart">
              <img
                src="https://pngimg.com/uploads/shopping_cart/shopping_cart_PNG38.png"
                width="50"
                alt
              />
              <span class="badge">{{ cart.length }}</span>
            </router-link>
          </div>
          <router-link v-else class="btn" to="/login">Login</router-link>
        </div>
      </nav>
    </div>
    <div class="page-wrapper">
      <router-view />
    </div>
  </div>
</template>
<script>
import {mapGetters} from 'vuex';
export default {
  name: 'Base',
  computed: {
    ...mapGetters('account', ['user']),
    ...mapGetters('product', ['cart']),
  },
};
</script>

<style></style>
