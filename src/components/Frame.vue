<template>
  <div
    v-if="imageUrl"
    class="main_div"
    :style="{ width: this.frame.w * this.zoom + 'px', height: this.frame.h * this.zoom + 'px' }"
  >
    <img :src="imageUrl" class="photo" />
  </div>
</template>

<script>
const zoom = 213
export default {
  props: {
    imageUrl: String,
    frame: Object,
    zoom: Number
  },
  data() {
    return {}
  }
}
</script>

<style scoped>
.main_div {
  background-color: red;
  display: flex;
  justify-content: center;
  align-items: center;
}

.photo {
  object-fit: cover;
  width: 100%;
  height: 100%;
}
</style>
