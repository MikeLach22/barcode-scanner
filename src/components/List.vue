<template>
    <li v-for="item in scannedProducts" id="product"><Product :productObject="item"></Product></li>
</template>

<script>
    import Product from "./Product.vue"

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
            /*axios.get("").then(response => {
                this.scannedProducts=response.data
            })*/
            this.scannedProducts.push({name: "Wasser", code:"4009228120077"}, {name:"Probiotika", code: "4260518460314"})
        }

    }
</script>

<style>
#product{
    list-style-type: none;
}
</style>