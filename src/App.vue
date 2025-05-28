<template>
  <div id="app">
    <!-- Background Video -->
    <video autoplay muted loop playsinline class="background-video">
      <source :src="videoSource" type="video/mp4" />
      Your browser does not support the video tag.
    </video>

    <!-- Page Content Overlay -->
    <div class="app-content">
      <Navigation />
      <router-view />
      <Footer />
    </div>
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue'
import Footer from './components/Footer.vue'
import videoFile from './assets/bg-video.mp4' // Ensure the filename matches

export default {
  name: 'App',
  components: {
    Navigation,
    Footer
  },
  data() {
    return {
      videoSource: videoFile
    }
  }
}
</script>

<style>
/* Reset body to remove white gaps */
body, html {
  margin: 0;
  padding: 0;
  height: 100%;
  overflow-x: hidden;
}

/* Entire app stretches full screen */
#app {
  position: relative;
  min-height: 100vh;
  overflow-x: hidden;
  overflow-y: auto;
}

/* Video as fullscreen background */
.background-video {
  position: fixed;
  top: 0;
  left: 0;
  min-width: 100vw;
  min-height: 100vh;
  width: auto;
  height: 100vh;
  object-fit: cover;
  z-index: -1;
  pointer-events: none;
}

/* Content floats over video */
.app-content {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background: transparent;
}

/* Optional: Remove any background in child pages */
router-view {
  flex: 1;
}
</style>
