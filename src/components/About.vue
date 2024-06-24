<template>
  <div class="about-container">
    <div class="about-content">
      <h1 class="about-title">Selamat Datang di Web Saya</h1>
      <p class="about-description">Saya Oga Jira Paltarest dari kelas 4F, saya asli pariaman namun besar di Pekanbaru, saya suka bermain Mobile Legend dan Matkul PBK adalah yang paling saya sukai</p>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style>
body {
  margin: 0;
  font-family: 'Arial', sans-serif;
}

.about-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-size: cover;
  background-position: center;
}

.about-content {
  text-align: center;
  background-color: rgba(0, 0, 0, 0.6); 
  padding: 30px;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
}

.about-title {
  font-size: 48px;
  font-weight: bold;
  color: #ffffff;
  margin-bottom: 20px;
  text-transform: uppercase;
  letter-spacing: 2px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7); 
}

.about-description {
  font-size: 20px;
  color: #ffffff;
  margin-bottom: 30px;
  line-height: 1.6;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.7); 
}
</style>
