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
            scanDeteced: false,
            productObject: { id: "", name: "", description: "", img: "" },
            failedScan: false
        };
    },
    methods: {
        onDecode(result) {
            axios.get('http://localhost:3000/Product', {
                params: {
                    prodId: result,
                }
            }).then(resp => {
                this.productObject = resp.data;
            }).catch(err => {
                this.failedScan = true;
            });
            this.scanDeteced = true;

        },
        rescan() {
            this.scanDeteced = false;
            this.productObject = { id: "", name: "", description: "", img: "" };
            this.failedScan = false;
        }
    },
};
</script>

<template>
    <div v-if="!scanDeteced" id="scanner">
        <v-card variant="outlined">
            <StreamBarcodeReader @decode="onDecode"></StreamBarcodeReader>
        </v-card>
    </div>
    <div v-if="scanDeteced">
        <Product :productObject="productObject"></Product>
        <div>
            <v-btn @click="rescan">Scan new item</v-btn>
            <v-chip v-if="!failedScan" id="recognized">Scan recognized</v-chip>
            <v-chip v-if="failedScan" id="notRecognized">Scan not recognized</v-chip>
        </div>
    </div>
</template>

<style>
#recognized {
    margin-left: 3%;
    color: green;
}

#notRecognized {
    margin-left: 3%;
    color: red;
}
</style>