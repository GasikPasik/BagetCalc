<template>
  <div class="main-div">
    <div class="size-div">
      <Slider
        nameField="Ширина"
        :minValue="10"
        :maxValue="150"
        :startValue="this.frame.w"
        @change-val="changeWidth"
      />
      <Slider
        nameField="Высота"
        :minValue="10"
        :maxValue="150"
        :startValue="this.frame.h"
        @change-val="changeHeight"
      />
      <div>Текущие габариты: {{ this.frame.w }}x{{ this.frame.h }}</div>
      <!-- <CheckBox title="Нужно ли магазин"></CheckBox> -->
    </div>
    <div></div>
  </div>
</template>

<script>
// import CheckBox from './UI/CheckBox.vue';
import Slider from './UI/Slider.vue'

export default {
  components: {
    Slider //, CheckBox
  },
  props: {
    frame: Object
  },
  methods: {
    changeWidth(newWidth) {
      this.frame.w = Number(newWidth)
      this.$emit('updateFrame', this.frame)
    },
    changeHeight(newHeight) {
      this.frame.h = Number(newHeight)
      this.$emit('updateFrame', this.frame)
    }
  }
}
</script>

<style scoped>
.main-div {
  background-color: rgb(70, 70, 70);
}

.size-div {
  display: flex;
  flex-direction: column;

  width: 100%;
  padding: 20px;
  gap: 15px;
}
</style>
