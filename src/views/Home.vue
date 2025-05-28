<template>
  <main>
    <HeroSection 
      title="Hi, I'm Mabel Zigah Ablah" 
      subtitle="A Software Engineer" 
    />
    
    <PortfolioGrid />
  </main>
</template>

<script>
import HeroSection from '../components/HeroSection.vue'
import PortfolioGrid from '../components/PortfolioGrid.vue'

export default {
  name: 'HomeView',
  components: {
    HeroSection,
    PortfolioGrid
  }
}
</script>