<template>
  <section class="hero">
    <div class="hero-container">
      <!-- Left: Image with GSAP animation -->
      <div class="image-wrapper" ref="imageWrapper">
        <div class="profile-circle" ref="profileCircle">
          <img :src="myPic" alt="Mabe Picture" class="profile-img" ref="profileImg" />
        </div>
      </div>

      <!-- Right: Text & Description Card -->
      <div class="text-content">
        <div class="text-card" ref="textCard">
          <h1>{{ title }}</h1>
          <p class="subtitle">{{ subtitle }}</p>
        </div>
        <div class="description-card" ref="descriptionCard">
          <h2>About Me</h2>
          <p>
            I'm passionate about Software Engineering, the craft of designing, 
            developing, and maintaining reliable and efficient software solutions. 
            It blends creativity with logic, allowing me to solve real-world problems through clean code, 
            thoughtful architecture, and scalable systems.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import myPic from '@/assets/mab1.jpg'

defineProps({
  title: String,
  subtitle: String
})

// Refs
const imageWrapper = ref(null)
const profileCircle = ref(null)
const profileImg = ref(null)
const textCard = ref(null)
const descriptionCard = ref(null)

onMounted(() => {
  // Animate profile image
  gsap.set(profileCircle.value, {
    transformPerspective: 1000,
    rotationY: 0,
  })

  gsap.from(profileImg.value, {
    duration: 1.5,
    scale: 0.8,
    rotation: -10,
    opacity: 0,
    ease: "back.out(1.7)"
  })

  gsap.to(profileCircle.value, {
    rotationY: 5,
    rotationX: 2,
    duration: 8,
    repeat: -1,
    yoyo: true,
    ease: "sine.inOut"
  })

  imageWrapper.value.addEventListener('mouseenter', () => {
    gsap.to(profileCircle.value, {
      rotationY: 15,
      rotationX: 8,
      scale: 1.05,
      duration: 0.8,
      ease: "elastic.out(1, 0.5)"
    })
  })

  imageWrapper.value.addEventListener('mouseleave', () => {
    gsap.to(profileCircle.value, {
      rotationY: 0,
      rotationX: 0,
      scale: 1,
      duration: 1.2,
      ease: "elastic.out(1, 0.3)"
    })
  })

  // Animate cards
  gsap.from(textCard.value, {
    x: 100,
    opacity: 0,
    duration: 1.2,
    ease: "power3.out",
    delay: 0.5
  })

  gsap.from(descriptionCard.value, {
    x: 100,
    opacity: 0,
    duration: 1.2,
    ease: "power3.out",
    delay: 0.9
  })
})
</script>

<style scoped>
.hero {
  min-height: 90vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
}

.hero-container {
  display: flex;
  align-items: flex-start;
  gap: 4rem;
  max-width: 1600px;
  background-color: rgba(255, 182, 193, 0.25);
  box-shadow: 0 8px 24px rgba(255, 105, 180, 0.2);
  padding: 2.5rem;
  border-radius: 30px;
  backdrop-filter: blur(12px);
  flex-wrap: wrap;
  border: #4a0033 solid 5px;
}

.image-wrapper {
  position: relative;
  width: 400px;
  height: 400px;
  perspective: 1000px;
  flex-shrink: 0;
}

.profile-circle {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  overflow: hidden;
  position: relative;
  box-shadow: 0 10px 30px rgba(216, 30, 91, 0.3);
  border: 6px solid #d81e5b;
  transform-style: preserve-3d;
  will-change: transform;
}

.profile-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  will-change: transform;
}

.text-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  min-width: 300px;
}

.text-card {
  background-color: rgba(255, 192, 203, 0.15);
  padding: 2rem 2.5rem;
  border-radius: 20px;
  box-shadow: 0 4px 12px rgba(255, 105, 180, 0.15);
  text-align: left;
  border: #4a0033 solid 2px;
}

.text-card h1 {
  font-size: 3rem;
  font-weight: 900;
  color: #d81e5b;
  margin-bottom: 1rem;
}

.text-card .subtitle {
  font-size: 1.3rem;
  color: #4a0033;
}

.description-card {
  background-color: rgba(255, 228, 240, 0.12);
  padding: 1.8rem 2rem;
  border-radius: 18px;
  box-shadow: 0 4px 12px rgba(255, 105, 180, 0.1);
  color: #4a0033;
  line-height: 1.7;
  border: #4a0033 solid 2px;
}

.description-card h2 {
  font-size: 1.6rem;
  margin-bottom: 0.8rem;
  color: #d81e5b;
}

/* Responsive */
@media (max-width: 1024px) {
  .hero-container {
    flex-direction: column;
    align-items: center;
  }

  .image-wrapper {
    width: 300px;
    height: 300px;
  }
}

@media (max-width: 768px) {
  .text-card, .description-card {
    text-align: center;
    padding: 1.5rem;
  }

  .text-card h1 {
    font-size: 2.2rem;
  }

  .text-card .subtitle,
  .description-card {
    font-size: 1.1rem;
  }
}
</style>
