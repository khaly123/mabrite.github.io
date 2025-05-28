<template>
  <footer id="contact" class="site-footer">
    <div class="container">
      
      <div class="copyright">
        <p>&copy; {{ currentYear }} Mabe Portfolio. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  data() {
    return {
      currentYear: new Date().getFullYear()
    }
  }
}
</script>

<style scoped>
.site-footer {
  color:  #4a0033 ;
  padding: 0.7rem 1px;
  margin-top: auto;
  border:  #4a0033  1px solid;
  background-color: rgba(255, 105, 180, 0.2);
  border-radius: 50px;
  margin-bottom: 20px;
  box-shadow: 0 8px 24px #ff006e;

}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.footer-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin-bottom: 2rem;
}

.footer-section h3 {
  margin-bottom: 1rem;
  font-size: 50px;
}

.footer-section p {
  margin: 0.5rem 0;
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-links a {
  color: #42b983;
  text-decoration: none;
}

.social-links a:hover {
  text-decoration: underline;
}

.copyright {
  text-align: center;
  padding-top: 1rem;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  font-size: 20px;
}
</style>