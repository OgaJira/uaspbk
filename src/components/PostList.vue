<script setup>
import { ref, onMounted } from 'vue'

const selectedUser = ref(null)
const users = ref([])
const posts = ref([])
const selectedUserName = ref('')

const fetchUsers = async () => {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/users')
    users.value = await response.json()
  } catch (error) {
    console.error('Error fetching users:', error)
  }
}

const fetchPosts = async () => {
  if (!selectedUser.value) return
  try {
    const response = await fetch(`https://jsonplaceholder.typicode.com/posts?userId=${selectedUser.value}`)
    posts.value = await response.json()
    selectedUserName.value = users.value.find(user => user.id === selectedUser.value)?.name || ''
  } catch (error) {
    console.error('Error fetching posts:', error)
  }
}

onMounted(fetchUsers)
</script>

<template>
  <section class="post-section">
    <h2 class="header-text">Postingan Pengguna</h2>
    <div class="select-user">
      <label for="user-select" class="select-label">Pilih Pengguna:</label>
      <select id="user-select" v-model="selectedUser" @change="fetchPosts" class="select-box">
        <option v-for="user in users" :key="user.id" :value="user.id">{{ user.name }}</option>
      </select>
    </div>
    <div v-if="posts.length > 0" class="user-posts">
      <h3 class="subheader-text">Postingan Pengguna: {{ selectedUserName }}</h3>
      <table class="post-table">
        <thead>
          <tr>
            <th>Judul</th>
            <th>Isi</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="post in posts" :key="post.id">
            <td>{{ post.title }}</td>
            <td>{{ post.body }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div v-else class="no-posts">
      <p>Tidak ada postingan yang tersedia.</p>
    </div>
  </section>
</template>

<style scoped>
.post-section {
  margin-top: 20px;
  padding: 20px;
  background: rgba(0, 0, 0, 0.5);
  border-radius: 10px;
  max-width: 800px;
  margin: 20px auto;
}

.select-user {
  margin-bottom: 20px;
  text-align: center;
}

.select-box {
  padding: 8px 12px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f8f8f8;
  transition: border-color 0.3s, background-color 0.3s;
}

.select-box:focus {
  outline: none;
  border-color: #007bff;
  background-color: white;
}

.user-posts {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.post-table {
  width: 100%;
  border-collapse: collapse;
}

.post-table th,
.post-table td {
  padding: 12px;
  border: 1px solid #ddd;
}

.post-table th {
  background-color: #f2f2f2;
}

.post-table td {
  background-color: white;
}

.post-table tr:hover {
  background-color: #f0f0f0;
}

.no-posts {
  text-align: center;
  margin-top: 20px;
  color: #ffffff;
}

.header-text, .subheader-text, .select-label {
  color: white;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.7);
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1; 
}
</style>
