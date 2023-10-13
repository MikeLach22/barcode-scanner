<script>
import { StreamBarcodeReader } from 'vue-barcode-reader';

export default {
    components: {
        StreamBarcodeReader
    },
    data() {
        return {
            code: '???'
        };
    },
    methods: { 
        onDecode(result) { 
            console.log(result)
            this.code=result
        }    
    },
};

</script>
<template>
    <StreamBarcodeReader @decode="onDecode" @loaded="onLoaded"></StreamBarcodeReader>

    <p>Barcode: {{ code }}</p>
</template>