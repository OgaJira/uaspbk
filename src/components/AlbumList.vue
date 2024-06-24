<template>
  <div class="AlbumDetails-container">
    <h2 class="header-text">Album</h2>
    <div v-if="albums.length">
      <table class="album-table">
        <tbody>
          <tr v-for="album in albums" :key="album.id" @click="viewAlbum(album.id)" class="album-item">
            <td class="album-id">{{ album.id }}</td>
            <td class="album-title">{{ album.title }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div v-else class="no-albums">
      <p>Tidak ada album yang tersedia.</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useAlbumsStore } from '../stores/albums'
import { useRouter } from 'vue-router'

const albumsStore = useAlbumsStore()
const albums = ref([])
const router = useRouter()

const fetchAlbums = async () => {
  await albumsStore.fetchAlbums()
  albums.value = albumsStore.albums
}

const viewAlbum = (id) => {
  router.push(`/albums/${id}`)
}

onMounted(fetchAlbums)
</script>

<style scoped>
body {
  margin: 0;
  font-family: 'Arial', sans-serif;
}

.AlbumDetails-container {
  display: flex;
  flex-direction:column;
  justify-content: left;
  align-items: left;
  min-height: 100vh;
  padding: 20px;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

.header-text {
  color: #ffffff;
  text-align: center;
  margin-bottom: 20px;
  font-size: 24px;
  font-weight: bold;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.7);
}

.album-table {
  width: 100%;
  max-width: 800px;
  border-collapse: separate;
  border-spacing: 0 10px;
  margin: 0 auto;
}

.album-item {
  cursor: pointer;
  transition: background-color 0.3s, color 0.3s;
}

.album-item:hover {
  background-color: #000000;
  color: white;
}

.album-id, .album-title {
  padding: 10px;
  border: 1px solid #ffffff;
}

.album-id {
  font-weight: bold;
}

.album-title {
  font-family: 'Arial', sans-serif;
}

.no-albums {
  text-align: center;
  margin-top: 20px;
  color: #ffffff;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.7);
}
</style>
