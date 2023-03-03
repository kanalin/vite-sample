<template>
    <div>
        產品列表
        <!-- {{ product }} -->
    <table>
        <tbody>
            <tr v-for="item in product" :key="item.id">
                <td>{{ item.title }} </td>
                <td><img :src="item.imageUrl" width="300" alt=""> </td>
                <td><RouterLink :to="`/product/${item.id}`">連結到單一產品頁面</RouterLink></td>
            </tr>
        </tbody>
    </table>
    </div>
</template>

<script>
    const site = 'https://vue3-course-api.hexschool.io/v2/';
    const apiPath = 'niniin';
    const url = `${site}api/${apiPath}/products/all`;

    import { RouterLink } from 'vue-router';

    export default {
        data(){
            return{
                product: [],
            }
        },
        components:{
            RouterLink,
        },
        mounted(){
            this.$http.get(url)
                .then(res => {
                    this.product = res.data.products;
                    console.log(this.product);
                })
                .catch(err=>{
                    alert("(getProducts) "+err.data.message);
                    console.log(err);
                })  
        }
    }
</script>