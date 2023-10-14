<script>
import { StreamBarcodeReader } from 'vue-barcode-reader';
import Product from './Product.vue'

export default {
    components: {
        StreamBarcodeReader,
        Product
    },
    data() {
        return {
            scanbool: false,
            productObject: {name: "", code:"", description:"", img:""},
            scannerWork: true
        };
    },
    methods: { 
        onDecode(result) { 
            console.log(result)
            /*axios.get("", {
                params: {
                    code: result
                },
            }).then(response => {
                this.productObject = response.data
                this.scanbool=true
            });*/
            if(result=='4009228120077'){
                this.productObject={name: "Wasser", code:"4009228120077", description:"this is a description"}
                this.scanbool=true
            }
        },
        rescan(){
            this.scanbool=false
            this.productObject={name: "", code:"", description:"", img:""}
        }  
    },
};

</script>
<template>
    
    <div v-show="!scanbool" id="scanner">
        <v-card variant="outlined">
            <StreamBarcodeReader @decode="onDecode"></StreamBarcodeReader>
        </v-card>
    </div>
    <div v-show="scanbool">
        <Product :productObject="productObject"></Product>
        <v-btn @click="rescan">Scan new item</v-btn>
    </div>
</template>

<style>
    
</style>