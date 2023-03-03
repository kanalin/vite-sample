<template>
    <div>
        單一產品頁面
        <table>
            <tbody>
                <tr>
                    <td>{{ product.title }}</td>
                    <td>{{ product.price }}</td>
                </tr>
                <tr>
                    <td></td>
                    <td>
                        <RouterLink to="/products" >回產品列表</RouterLink>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    const site = 'https://vue3-course-api.hexschool.io/v2/';
    const apiPath = 'niniin';
    // let url = `${site}api/${apiPath}/product`;

    import { RouterLink } from 'vue-router';

    export default{
        data(){
            return{
                product:{},
            }
        },
        mounted(){
            // console.log(this.$route.params.id);   // 單純的值(屬性值)
            // console.log(this.$router);  // 方法
            
            const { id } = this.$route.params;   // 取得id
            // this.$router.push(`/${id}`);     //切換頁面
            const url = `${site}api/${apiPath}/product/${id}`;
            this.$http.get(url)
                    .then(res => {
                        this.product = res.data.product;
                        console.log(res.data);
                    })
                    .catch(err=>{
                        alert("(getProduct) "+err.data);
                        console.log(err);
                    })  
        }
    }
</script>