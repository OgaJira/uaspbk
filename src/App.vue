<template>
  <div>
    <header class="header">
      <nav class="menu">
        <ul>
          <li><router-link to="/">Home</router-link></li>
          <li><router-link to="/todos">Todos</router-link></li>
          <li><router-link to="/posts">Posts</router-link></li>
          <li><router-link to="/albums">Albums</router-link></li>
          <li><router-link to="/about">About</router-link></li>
        </ul>
      </nav>
    </header>
    <router-view></router-view>
  </div>
</template>

<style>
body {
  margin: 0;
  font-family: 'Arial', sans-serif;
  background: linear-gradient(135deg, #f0f0f0, #c0c0c0);
}

.header {
  background: linear-gradient(135deg, #255b7c, #103f5c);
  padding: 20px;
  text-align: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.menu ul {
  display: flex;
  justify-content: center;
  list-style: none;
  padding: 0;
  margin: 0;
}

.menu ul li {
  margin: 0 15px;
}

.menu ul li a {
  text-decoration: none;
  color: #ffffff; 
  font-weight: bold;
  font-size: 20px; 
  padding: 10px 20px; 
  border-radius: 20px; 
  transition: background-color 0.3s, transform 0.3s, box-shadow 0.3s; 
}

.menu ul li a:hover {
  background-color: #ffffff; 
  color: #255b7c;
  transform: scale(1.1); 
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.menu ul li a:active {
  transform: scale(0.95);
}

.router-link-exact-active {
  background-color: #103f5c;
  color: #ffffff;
  border-radius: 20px;
}
</style>
