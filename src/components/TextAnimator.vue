<template>
  <h1 class="hero-title">
    <span v-for="(char, index) in animatedText" :key="index" :style="{ animationDelay: `${index * 0.1}s` }">
      {{ char === ' ' ? '&nbsp;' : char }}
    </span>
  </h1>
</template>

<script>
export default {
  name: 'TextAnimator',
  props: {
    text: {
      type: String,
      required: true
    }
  },
  computed: {
    animatedText() {
      return this.text.split('')
    }
  }
}
</script>

<style scoped>
.hero-title {
  font-size: 2.5rem;
  margin: 0;
  overflow: hidden;
}

.hero-title span {
  display: inline-block;
  opacity: 0;
  animation: fadeIn 0.5s forwards;
}

@keyframes fadeIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
  from {
    opacity: 0;
    transform: translateY(20px);
  }
}
</style>