<template>
    這是前台產品列表頁面
    <br>
    <br>
    <table class="table">
        <thead>
            <tr>
                <th>名稱</th>
                <th>圖片</th>
                <th>連結</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="item in product" :key="item.id+1">
                <td>{{ item.title }}</td>
                <td><img :src="item.imageUrl" width="200" alt=""></td>
                <td><RouterLink :to="`/product/${item.id}`">詳細內容</RouterLink></td>
            </tr>
        </tbody>
    </table>
</template>

<script>
import { RouterLink } from 'vue-router'
const { VITE_APP_URL, VITE_APP_PATH } = import.meta.env
export default {
  data () {
    return {
      product: []
    }
  },
  methods: {
    getProducts () {
      this.$http.get(`${VITE_APP_URL}api/${VITE_APP_PATH}/products/all`)
        .then(res => {
          this.product = res.data.products
        //   console.log(this.product)
        })
        .catch(err => {
          alert(err.data.message)
        //   console.log(err)
        })
    }
  },
  components: {
    RouterLink
  },
  mounted () {
    this.getProducts()
  }
}
</script>
