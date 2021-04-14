<template>
  <div class="container row">
    <div v-for="chunk in chunkedImages" :key="chunk">
      <div class="giphy-image" v-for="image in chunk" :key="image">
        <img :src="image.images.fixed_width.url" :alt="image.title" :title="image.title" />
      </div>
    </div>
  </div>
</template>
<script>
var _ = require("lodash");
export default {
  name: "GifCollection",
  props: {
    collection: Array,
  },
  computed: {
    chunkedImages: function() {
      const chunkSize = this.collection.length / 6;
      return _.chunk(this.collection, chunkSize);
    },
  },
};
</script>

<style scoped>
.container {
  margin-top: 40px;
  width: 1200px;
  margin: auto;
}
.row {
  display: flex;
  flex-wrap: wrap;
  padding: 0 4px;
}
.column {
  flex: 25%;
  padding: 0 4px;
}
.column img {
  margin-top: 8px;
  vertical-align: middle;
}
</style>
