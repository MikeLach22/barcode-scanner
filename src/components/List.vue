<template>
    <li v-for="item in scannedProducts" id="product"><Product :productObject="item"></Product></li>
</template>

<script>
    import Product from "./Product.vue"
    import axios from 'axios'

    export default{
        data() {
            return{
                scannedProducts: []
            }
        },
        components: {
            Product
        },
        mounted(){
            axios.get('http://localhost:3000/ProductList/',{
            }).then(response => {
                this.scannedProducts=response.data  
            })
        }

    }
</script>

<style>
#product{
    list-style-type: none;
}
</style>