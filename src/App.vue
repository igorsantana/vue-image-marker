<template>
  <div>
    <input
      type="file"
      accept="image/x-png,image/gif,image/jpeg"
      @change="getFile"
    />
    <img
      src=""
      ref="imageTag"
      class="image-size"
      @mousemove="hoverImage"
      :style="imgStyle"
    />
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      imgStyle: {
        display: "none",
      },
    };
  },
  created() {
    const { imageTag } = this.$refs;
    imageTag.styl;
  },
  methods: {
    getFile(event) {
      const { files } = event.target;
      const [image] = files;
      const { imageTag } = this.$refs;
      const reader = new FileReader();
      reader.onloadend = () => (imageTag.src = reader.result);
      reader.readAsDataURL(image);
      this.imgStyle = { display: "block" };
    },
    hoverImage(event) {
      console.log(event);
    },
  },
};
</script>

<style scoped>
img.image-size {
  width: 500px;
  height: 500px;
}
</style>
