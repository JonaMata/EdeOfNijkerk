<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header>
    <nav>
      <div class="nav-left">
        <h2>Ede of Nijkerk?</h2>
      </div>
      <div class="nav-right">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </div>
    </nav>
  </header>
  <div class="container">
    <RouterView />
  </div>
</template>

<style lang="scss">
body {
  margin: 0;
  font-family: Roboto, sans-serif;
}

header {
  background: #3dbaff;
}

nav {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 0 10px;
}

nav a {
  margin: 0 5px;
  color: white;

  &:hover {
    text-decoration-thickness: 3px;
  }
}

.container {
  width: 80%;
  margin: 20px auto;
  padding: 5px;
}
</style>
