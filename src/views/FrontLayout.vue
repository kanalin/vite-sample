<template>
    <div class="container">
        LOGO
        <router-link to="/">首頁</router-link> |
        <router-link to="/about">關於我</router-link> |
        <router-link to="/products">產品列表</router-link> |
        <router-link to="/cart">購物車</router-link>
        <hr>
        <RouterView></RouterView>
    </div>
</template>

<script>
import { RouterView } from 'vue-router'

export default {
  components: {
    RouterView
  }
}
</script>
