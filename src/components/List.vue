<template>
    <li v-for="item in scannedProducts"><Product :productObject="item"></Product></li>
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