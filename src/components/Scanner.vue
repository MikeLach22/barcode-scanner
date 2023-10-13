<script>
import { StreamBarcodeReader } from 'vue-barcode-reader';

export default {
    components: {
        StreamBarcodeReader
    },
    data() {
        return {
        };
    },
    methods: { 
        onDecode(result) { 
            console.log(result)
        }    
    },
};

</script>
<template>
    <StreamBarcodeReader @decode="onDecode" @loaded="onLoaded"></StreamBarcodeReader>
</template>