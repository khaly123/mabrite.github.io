<template>
  <div class="custom-cursor" :style="cursorStyle"></div>
</template>

<script>
export default {
  name: 'CustomCursor',
  data() {
    return {
      x: 0,
      y: 0,
    }
  },
  computed: {
    cursorStyle() {
      return {
        left: `${this.x}px`,
        top: `${this.y}px`
      }
    }
  },
  mounted() {
    window.addEventListener('mousemove', this.updateCursor)
  },
  beforeUnmount() {
    window.removeEventListener('mousemove', this.updateCursor)
  },
  methods: {
    updateCursor(e) {
      this.x = e.clientX
      this.y = e.clientY
    }
  }
}
</script>

<style scoped>
.custom-cursor {
  position: fixed;
  top: 0;
  left: 0;
  width: 18px;
  height: 18px;
  background-color: transparent;
  border: 2px solid white;
  border-radius: 50%;
  pointer-events: none;
  transform: translate(-50%, -50%);
  transition: transform 0.1s ease;
  z-index: 9999;
}
</style>
