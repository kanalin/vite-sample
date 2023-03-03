<template>
    這是前台單一產品頁面
    <br>
    <br>
    <table class="table">
        <thead>
            <tr>
                <th>名稱</th>
                <th>價格</th>
                <th>說明</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>{{ product.title }}</td>
                <td>{{ product.price }}</td>
                <td>{{ product.content }}</td>
            </tr>
            <tr>
            </tr>
        </tbody>
    </table>
    <RouterLink to="/products" >回產品列表</RouterLink>
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
  components: {
    RouterLink
  },
  mounted () {
    const { id } = this.$route.params
    this.$http.get(`${VITE_APP_URL}api/${VITE_APP_PATH}/product/${id}`)
      .then(res => {
        this.product = res.data.product
        // console.log(this.product)
      })
      .catch(err => {
        alert(err.data.message)
        // console.log(err)
      })
  }
}
</script>
