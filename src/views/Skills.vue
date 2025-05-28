<template>
  <main class="skills-page">
    <HeroSection title="My Skills" subtitle="Technologies I work with and my proficiency levels" />
    
    <section class="skills-section">
      <div class="container">
        <div class="skills-container">
          <div class="skill-category" v-for="category in skillCategories" :key="category.title">
            <h3>{{ category.title }}</h3>
            <div class="skills-grid">
              <div class="skill-item" v-for="skill in category.skills" :key="skill.name">
                <div class="skill-icon">
                  <span>{{ skill.emoji || '💻' }}</span>
                </div>
                <div class="skill-info">
                  <h4>{{ skill.name }}</h4>
                  <div class="skill-level">
                    <div class="level-bar" :style="{ width: skill.level + '%' }"></div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
import HeroSection from '../components/HeroSection.vue'

export default {
  name: 'SkillsPage',
  components: {
    HeroSection
  },
  data() {
    return {
      skillCategories: [
        {
          title: 'Frontend Development',
          skills: [
            { name: 'Vue.js', level: 90, emoji: '⚡' },
            { name: 'React', level: 85, emoji: '⚛️' },
            { name: 'JavaScript', level: 95, emoji: '📜' },
            { name: 'HTML/CSS', level: 98, emoji: '🎨' }
          ]
        },
        {
          title: 'Backend Development',
          skills: [
            { name: 'Node.js', level: 80, emoji: '🖥️' },
            { name: 'Express', level: 75, emoji: '🚂' },
            { name: 'MongoDB', level: 70, emoji: '🍃' }
          ]
        },
        {
          title: 'Tools & Design',
          skills: [
            { name: 'Git', level: 85, emoji: '🐙' },
            { name: 'Figma', level: 80, emoji: '✏️' },
            { name: 'Photoshop', level: 70, emoji: '🎭' }
          ]
        }
      ]
    }
  }
}
</script>

<style scoped>
.skills-page {
  padding-top: 60px;
}

.skills-section {
  padding: 4rem 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.skills-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.skill-category {
  background: #4a0033;
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.skill-category h3 {
  margin-bottom: 1.5rem;
  color: #ff006e;
}

.skills-grid {
  display: grid;
  gap: 1rem;
}

.skill-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  color: lavender;
}

.skill-icon {
  font-size: 1.5rem;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: ivory;
  border-radius: 50%;
}

.skill-info {
  flex: 1;
}

.skill-info h4 {
  margin: 0 0 0.3rem 0;
  font-size: 1rem;
}

.skill-level {
  height: 6px;
  background: ivory;
  border-radius: 3px;
  overflow: hidden;
}

.level-bar {
  height: 100%;
  background: #ff006e;
  transition: width 1s ease-in-out;
}
</style>