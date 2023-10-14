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
            productObject: {id:"",name:"",description:"",img:""},
            scannerWork: true,
            fail: false
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
            }).catch(err => {
                console.log(err);
                this.fail = true;
            });
            this.scanbool=true;

        },
        rescan(){
            this.scanbool=false
            this.productObject={name: "", code:""}
            this.scanbool=false;
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
        <div>
            <v-btn @click="rescan">Scan new item</v-btn>
            <v-chip v-if="!fail" id="recognized">Scan recognized</v-chip>
            <v-chip v-if="fail" id="notRecognized">Scan not recognized</v-chip>
        </div>
        
        
    </div>

</template>

<style>
    #recognized{
        margin-left: 3%;
        color: green;
    }
    #notRecognized{
        margin-left: 3%;
        color: red;
    }
</style>