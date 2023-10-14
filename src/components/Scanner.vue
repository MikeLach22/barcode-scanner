<script>
import { StreamBarcodeReader } from 'vue-barcode-reader';
import Product from './Product.vue'
import axios from 'axios'

export default {
    components: {
        StreamBarcodeReader,
        Product
    },
    data() {
        return {
            scanbool: false,
            productObject: {id:0,name:"",description:"",img:""},
            scannerWork: true
        };
    },
    methods: { 
        onDecode(result) { 
            console.log(result)
            axios.get('http://localhost:3000/Product/',{
                params:{
                    Prodid: result,
            }
            }).then(resp => {
                console.log(resp.data);
                this.productObject=resp.data;
            });
            this.scanbool=true;
        },
        rescan(){
            this.scanbool=false
            this.productObject={name: "", code:""}
        }  
    },
};

</script>
<template>
    
    <div v-if="!scanbool" id="scanner">
        <v-card variant="outlined">
            <StreamBarcodeReader @decode="onDecode"></StreamBarcodeReader>
        </v-card>
    </div>
    <div v-if="scanbool">
        <Product :productObject="productObject"></Product>
        <v-btn @click="rescan">Scan new item</v-btn>
    </div>
</template>

<style>
    
</style>