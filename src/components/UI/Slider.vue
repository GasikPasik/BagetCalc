<template>
  <div class="main-div">
    <div class="nameField">{{ nameField }}</div>
    <div class="slider">
      <input
        type="range"
        :min="minValue"
        :max="maxValue"
        v-model="sliderValue"
        class="slider-input"
        step="0.1"
        @input="updateFromSlider"
      />
      <input
        v-if="isInput"
        class="input-value"
        v-model="inputValue"
        @input="validateInput"
        @blur="endInput"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    nameField: {
      type: String,
      default: ''
    },
    minValue: {
      type: Number,
      default: 10
    },
    maxValue: {
      type: Number,
      default: 150
    },
    startValue: {
      type: Number,
      default: 50
    },
    isInput: {
      type: Boolean,
      default: true
    }
  },
  data() {
    return {
      sliderValue: this.startValue,
      inputValue: this.startValue
    }
  },
  methods: {
    validateInput() {
      if (this.inputValue === '') return

      this.inputValue = this.inputValue.replace(',', '.')
      this.inputValue = this.inputValue.replace(/[^\d.]/g, '')
      if (this.inputValue.length > 5) this.inputValue = this.inputValue.slice(0, 5)

      var correctValue = this.inputValue

      if (correctValue < this.minValue) {
        correctValue = this.minValue
      } else if (correctValue > this.maxValue) {
        correctValue = this.maxValue
      }

      if (correctValue.indexOf('.') !== -1) correctValue = parseFloat(correctValue).toFixed(1)

      this.sliderValue = correctValue
      this.$emit('changeVal', correctValue)
    },
    endInput() {
      if (this.inputValue === '' || this.inputValue < this.minValue) {
        this.inputValue = this.minValue.toString()
      } else if (this.inputValue > this.maxValue) {
        this.inputValue = this.maxValue.toString()
      }
      if (this.inputValue.indexOf('.') !== -1)
        this.inputValue = parseFloat(this.inputValue).toFixed(1)
    },
    updateFromSlider() {
      this.inputValue = this.sliderValue
      this.$emit('changeVal', this.sliderValue)
    }
  }
}
</script>

<style scoped>
.main-div {
  flex-direction: column;
}
.slider {
  display: flex;
  flex-direction: row;

  gap: 10px;
}
.slider-input {
  width: 100%;
}
.input-value {
  min-width: 35px;
  max-width: 50px;
  height: 25px;
  text-align: center;
}
</style>
