<template>
  <div>
    <h2 style="color: #007bff; text-align: center;">Choose Album:</h2>
    <select v-model="selectedAlbum" @change="fetchPhotos" style="margin: 0 auto; display: block;">
      <option v-for="album in albums" :key="album.id" :value="album.id">{{ album.title }}</option>
    </select>
    <h2 style="color: #007bff; text-align: center;">Photos in Album {{ selectedAlbum }}</h2>
    <table v-if="photos.length" style="margin: 0 auto;">
      <thead>
        <tr>
          <th>Thumbnail</th>
          <th>Title</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="photo in photos" :key="photo.id" style="text-align: center;">
          <td>
            <img :src="photo.thumbnailUrl" @click="showPhoto(photo.url)" style="width: 100px; height: 100px; object-fit: cover; border: 1px solid #007bff; border-radius: 5px; cursor: pointer; transition: border-color 0.3s;">
          </td>
          <td>{{ photo.title }}</td>
        </tr>
      </tbody>
    </table>
    <div v-else style="text-align: center; margin-top: 20px;">
      <p>No photos available.</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const selectedAlbum = ref(route.params.id)
const albums = ref([])
const photos = ref([])

const fetchAlbums = async () => {
  try {
    const response = await fetch(`https://jsonplaceholder.typicode.com/albums`)
    albums.value = await response.json()
  } catch (error) {
    console.error('Error fetching albums:', error)
  }
}

const fetchPhotos = async () => {
  try {
    const response = await fetch(`https://jsonplaceholder.typicode.com/albums/${selectedAlbum.value}/photos`)
    photos.value = await response.json()
  } catch (error) {
    console.error('Error fetching photos:', error)
  }
}

const showPhoto = (url) => {
  window.open(url, '_blank')
}

onMounted(() => {
  fetchAlbums()
  fetchPhotos()
})
</script>

<style scoped>
body {
  margin: 0;
  font-family: 'Arial', sans-serif;
}

.AlbumDetails-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  padding: 20px;
  font-weight: bold ;
}

.header-text {
  color: #007bff;
  text-align: center;
  margin-bottom: 20px;
  font-size: 24px;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.7);
}

.album-select {
  margin: 0 auto 20px auto;
  display: block;
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
  border: 1px solid #007bff;
  background-color: rgba(255, 255, 255, 0.8);
}

.photos-table {
  margin: 0 auto;
  width: 80%;
  border-collapse: collapse;
  background-color: rgba(255, 255, 255, 0.8);
  border-radius: 5px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.photos-table th, .photos-table td {
  padding: 10px;
  text-align: center;
  border: 1px solid #007bff;
}

.thumbnail-img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border: 1px solid #007bff;
  border-radius: 5px;
  cursor: pointer;
  transition: border-color 0.3s;
}

.thumbnail-img:hover {
  border-color: #0056b3;
}

.no-photos {
  text-align: center;
  margin-top: 20px;
  color: #ffffff;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.7);
}
</style>