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
            productObject: {name: "", code:""},
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
                this.productObject={name: "Wasser", code:"4009228120077"}
                this.scanbool=true
            }
        },
        rescan(){
            this.scanbool=false
            this.productObject={name: "", code:""}
        }  
    },
};

</script>
<template>
    
    <div v-show="!scanbool">
        <v-card>
            <StreamBarcodeReader @decode="onDecode"></StreamBarcodeReader>
        </v-card>
    </div>
    
        
    <div v-show="scanbool">
        <Product :productObject="productObject"></Product>
        <button @click="rescan">Scan new item</button>
    </div>
</template>