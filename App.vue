<template>
  <div>
  
    <AppNavbar />

    <main class="container py-5 fade-in">
      <RouterView />
    </main>
  </div>
</template>

<script setup>
import AppNavbar from './components/AppNavbar.vue'
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');


body {
  background: linear-gradient(to right, #c0dbffff, #e1f5ffff);
  font-family: 'Poppins', sans-serif;
  color: #333;
  margin: 0;
}

main.container {
  background: #fff;
  border-radius: 1rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  padding: 2rem;
  margin-top: 2rem;
  transition: all 0.3s ease;
}

.navbar {
  background: linear-gradient(90deg, #6973ffff, #f7faffff);
  font-weight: 500;
  letter-spacing: 0.5px;
}

.navbar-brand {
  font-weight: 600;
  color: #fffefe !important;
  font-size: 1.25rem;
}

.nav-link {
  color: #734d93 !important;
  opacity: 0.85;
  transition: 0.2s;
}

.nav-link:hover {
  opacity: 1;
  text-decoration: underline;
}

.fade-in {
  animation: fadeIn 0.8s ease-in-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
