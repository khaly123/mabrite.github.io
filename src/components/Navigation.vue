<template>
  <nav class="navigation" role="navigation" aria-label="Main Navigation">
    <div class="container">
      <router-link to="/" class="logo" aria-label="MABE Home">
        Welcome To My Portfolio
      </router-link>

      <button
        class="hamburger"
        @click="isMenuOpen = !isMenuOpen"
        :aria-expanded="isMenuOpen.toString()"
        aria-label="Toggle navigation menu"
      >
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </button>

      <div :class="['nav-links', { open: isMenuOpen }]">
        <router-link to="/" exact-active-class="active-tab" class="tab-card" @click="isMenuOpen = false">Home</router-link>
        <router-link to="/skills" exact-active-class="active-tab" class="tab-card" @click="isMenuOpen = false">Skills</router-link>
        <router-link to="/contact" exact-active-class="active-tab" class="tab-card" @click="isMenuOpen = false">Contact</router-link>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navigation',
  data() {
    return {
      isMenuOpen: false,
    };
  },
}
</script>

<style scoped>
/* Navigation base */
.navigation {
  position: sticky;
  top: 0;
  z-index: 110;
  width: 100%;
  padding: 1.5rem 0;
  backdrop-filter: blur(15px);
  background-color: rgba(255, 192, 203, 0.35);
  border-radius: 30px;
  box-shadow: 0 8px 24px rgba(255, 105, 180, 0.2);
  border: #4a0033 solid 2px;
  margin-top: 10px;
  animation: fadeInDown 0.6s ease forwards;
}

/* Container flex layout */
.container {
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  padding: 0 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* Logo */
.logo {
  font-family: 'Poppins', sans-serif;
  font-weight: 900;
  font-size: 1.8rem;
  color: #d81e5b;
  text-decoration: none;
  letter-spacing: 0.12em;
  transition: color 0.3s ease;
}
.logo:hover {
  color: #ff4d94;
}

/* Nav links */
.nav-links {
  display: flex;
  gap: 1rem;
}
.tab-card {
  position: relative;
  display: inline-block;
  padding: 0.6rem 1.4rem;
  background: rgba(255, 182, 193, 0.75);
  border-radius: 15px;
  font-weight: 600;
  color: #4a0033;
  text-decoration: none;
  box-shadow: 0 3px 6px rgba(255, 105, 180, 0.35);
  transition: color 0.3s ease, background-color 0.3s ease, transform 0.3s cubic-bezier(0.25, 1, 0.5, 1);
}
.tab-card:hover {
  background-color: #ff6699;
  color: white;
  transform: translateY(-4px) scale(1.05);
  box-shadow: 0 8px 16px rgba(255, 105, 180, 0.5);
}
.active-tab {
  background-color: #d81e5b;
  color: white;
  box-shadow: 0 8px 20px rgba(216, 30, 91, 0.6);
  transform: translateY(-4px) scale(1.1);
  pointer-events: none;
  font-weight: 700;
}

/* Hamburger button */
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
}
.bar {
  width: 25px;
  height: 3px;
  background-color: #4a0033;
  border-radius: 2px;
  transition: 0.3s ease;
}

/* Mobile Styles */
@media (max-width: 768px) {
  .nav-links {
    position: absolute;
    top: 100%;
    right: 0;
    background-color: rgba(255, 182, 193, 0.95);
    border: 2px solid #d81e5b;
    border-radius: 10px;
    flex-direction: column;
    gap: 0;
    width: 100px;
    display: none;
    padding: 1rem;
    box-shadow: 0 8px 16px rgba(255, 105, 180, 0.5);
    margin-top: 1rem;
  }
  .nav-links.open {
    display: flex;
  }
  .tab-card {
    width: 100%;
    text-align: left;
    margin-bottom: 0.5rem;
  }
  .hamburger {
    display: flex;
  }
}

/* Animation */
@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
