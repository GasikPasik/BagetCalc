<template>
  <div class="main-div">
    <div class="top-div">
      <input type="file" @change="handleFileUpload" />

      <Slider
        :isInput="false"
        :minValue="1"
        :maxValue="25"
        :startValue="this.zoom"
        @change-val="changeZoom"
      />
    </div>

    <div class="center-div">
      <Frame :frame="this.frame" :imageUrl="this.imageUrl" :zoom="this.zoom"></Frame>
    </div>
  </div>
</template>

<script>
import Frame from './Frame.vue'
import Slider from './UI/Slider.vue'

export default {
  components: {
    Frame,
    Slider
  },
  props: {
    frame: Object
  },
  data() {
    return {
      zoom: 2,
      imageUrl: null
    }
  },
  methods: {
    changeZoom(newZoom) {
      this.zoom = Number(newZoom)
    },
    handleFileUpload(event) {
      const file = event.target.files[0]
      if (file) {
        this.imageUrl = URL.createObjectURL(file)
      }
    }
  }
}
</script>

<style scoped>
.main-div {
  background-color: rgb(173, 173, 173);
  flex-direction: column;
  padding: 25px;
}
.top-div {
  align-self: flex-start;
}

.center-div {
  align-self: center;
  margin: auto;
}
</style>
