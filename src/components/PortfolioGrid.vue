<template>
  <section class="portfolio-section">
    <h2>My Projects</h2>
    <div class="portfolio-grid">
      <a
        v-for="project in projects"
        :key="project.title"
        :href="project.link"
        target="_blank"
        rel="noopener noreferrer"
        class="portfolio-item"
      >
        <img :src="project.thumbnail" :alt="project.title" class="project-thumbnail" />
        <div class="project-overlay">
          <h3>{{ project.title }}</h3>
          <p>{{ project.tags.join(', ') }}</p>
        </div>
      </a>
    </div>
  </section>
</template>

<script>
export default {
  name: 'PortfolioGrid',
  data() {
    return {
      projects: [
        {
          title: 'E-commerce Platform',
          thumbnail: 'https://images.pexels.com/photos/4968392/pexels-photo-4968392.jpeg?auto=compress&cs=tinysrgb&w=800',
          tags: ['Vue', 'Node.js', 'MongoDB'],
          link: 'https://your-ecommerce-project-link.com'
        },
        {
          title: 'Task Management App',
          thumbnail: 'https://images.pexels.com/photos/7693661/pexels-photo-7693661.jpeg?auto=compress&cs=tinysrgb&w=800',
          tags: ['React', 'Firebase'],
          link: 'https://your-task-app-link.com'
        },
        {
          title: 'Portfolio Website',
          thumbnail: 'https://images.pexels.com/photos/6476266/pexels-photo-6476266.jpeg?auto=compress&cs=tinysrgb&w=800',
          tags: ['Vue', 'GSAP'],
          link: 'https://your-portfolio-link.com'
        },
        {
          title: 'Weather Dashboard',
          thumbnail: 'https://images.pexels.com/photos/69903/pexels-photo-69903.jpeg?auto=compress&cs=tinysrgb&w=800',
          tags: ['JavaScript', 'API'],
          link: 'https://your-weather-dashboard-link.com'
        }
      ]
    }
  }
}
</script>

<style scoped>
.portfolio-section {
  padding: 4rem 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.portfolio-section h2 {
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2rem;
  color: #ff006e;
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

.portfolio-item {
  position: relative;
  display: block;
  border-radius: 8px;
  overflow: hidden;
  text-decoration: none;
  cursor: pointer;
  transition: transform 0.3s ease;
  aspect-ratio: 4/3;
  color: inherit;
}

.portfolio-item:hover {
  transform: translateY(-5px);
}

.project-thumbnail {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.project-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: #4a0033;
  color: lavender;
  padding: 1rem;
  transform: translateY(100%);
  transition: transform 0.3s ease;
}

.portfolio-item:hover .project-overlay {
  transform: translateY(0);
}

.project-overlay h3 {
  margin: 0 0 0.5rem;
  font-size: 1.25rem;
}

.project-overlay p {
  margin: 0;
  font-size: 0.9rem;
}
</style>
