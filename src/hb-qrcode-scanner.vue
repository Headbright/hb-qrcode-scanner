<template>
  <input ref="fileInput" type="file" @change="onImageAdded" />
</template>

<script>
  import jsQR from "jsqr";
  import { imageDataFromFile } from "./misc/image-data.js";
  export default {
    name: "HbQrcodeScanner",
    methods: {
      async onImageAdded() {
        const file = this.$refs.fileInput.files[0];
        try {
          const imageData = await imageDataFromFile(file)
          const result = jsQR(
                  imageData.data,
                  imageData.width,
                  imageData.height,
                  {
                    inversionAttempts: "dontInvert"
                  }
          );
          this.$emit('detect', result)
        } catch(err) {
          console.log(err)
          this.$emit( 'detect', null)
        }
      }
    }
  };
</script>
