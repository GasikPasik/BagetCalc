<template>
  <div class="main-div">
    <div class="left-div">
      <LogoBar></LogoBar>
      <ScreenFrame class="tmp" :frame="this.frame"></ScreenFrame>
    </div>

    <div class="right-div">
      <Menu :frame="this.frame" @update-frame="updateFrame"></Menu>
    </div>
  </div>
</template>

<script>
import ScreenFrame from '@/components/ScreenFrame.vue'
import Menu from './components/Menu.vue'
import LogoBar from './components/LogoBar.vue'

export default {
  components: {
    Menu,
    ScreenFrame,
    LogoBar
  },
  data() {
    return {
      frame: {
        // default value
        w: 40.0,
        h: 20.0
      }
    }
  },
  methods: {
    updateFrame(newFrame) {
      this.frame = newFrame
    }
  }
}
</script>

<style scoped>
.main-div {
  display: flex;
  height: 100vh;
}
.left-div {
  flex-direction: column;
  display: flex;
  flex: 1;
  height: 100%;
}
.right-div {
  flex: 1;
  max-width: 400px;
  width: 30%;
}
@media (max-width: 850px) {
  .main-div {
    flex-direction: column;
  }
  .right-div,
  .left-div {
    width: 100%;
    max-width: none;
  }
  .left-div {
    height: 60%;
  }
}
</style>
