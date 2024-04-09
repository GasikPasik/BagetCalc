<template>
  <div class="main-div">
    <div class="name-field">{{ title }}</div>
    <input type="checkbox" class="checkbox" :checked="isChecked" @change="handleChange" />
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    value: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      isChecked: this.value
    }
  },
  methods: {
    handleChange(event) {
      this.isChecked = event.target.checked
      // this.$emit('input', this.isChecked);
    }
  }
}
</script>

<style scoped>
.main-div {
  display: flex;
  justify-content: space-between;
}
.name-field {
  align-self: flex-start;
}

.checkbox {
  align-self: flex-end;
}
</style>
