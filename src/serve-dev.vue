<script>
import Vue from 'vue';
import HbQrcodeScanner from '@/hb-qrcode-scanner.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    HbQrcodeScanner
  }
});
</script>

<template>
  <div id="app">
    <hb-qrcode-scanner />
  </div>
</template>
