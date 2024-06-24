<template>
  <div class="home-container">
    <div class="home-content">
      <h1 class="home-title">UAS PBK TEORI OGA JIRA PALTAREST</h1>
      <p class="home-description">Silahkan lihat tentang saya dibawah ini</p>
      <router-link to="/about" class="btn" @click="handleAboutClick">Tentang Saya</router-link>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    handleAboutClick() {
      this.$router.push('/about');
    }
  }
}
</script>

<style scoped>
.home-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-image: linear-gradient(to right top, #30cfd0, #330867);
  background-size: cover;
  background-position: center;
  position: relative;
}

.home-content {
  text-align: center;
  color: #fff;
  z-index: 1;
  max-width: 600px;
}

.home-title {
  font-size: 48px;
  font-weight: bold;
  margin-bottom: 20px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.home-description {
  font-size: 20px;
  line-height: 1.6;
  margin-bottom: 30px;
}

.btn {
  padding: 12px 24px;
  background-color: #f95738;
  color: #fff;
  text-decoration: none;
  border-radius: 5px;
  transition: background-color 0.3s, transform 0.2s;
  display: inline-block;
}

.btn:hover {
  background-color: #ff5733;
  transform: translateY(-2px);
}
</style>
