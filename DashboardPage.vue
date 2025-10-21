<template>
  <div class="card shadow-sm mx-auto" style="max-width: 600px;">
    <div class="card-body text-center">
      <h1 class="h4 mb-3">Welcome, {{ user?.name || 'User' }} 👋</h1>

      <p class="text-muted">You are successfully logged in.</p>

      <ul class="list-group text-start mt-4">
        <li class="list-group-item">
          <strong>Username:</strong> {{ user?.username }}
        </li>
        <li class="list-group-item">
          <strong>Email:</strong> {{ user?.email }}
        </li>
        <li class="list-group-item">
          <strong>ID:</strong> {{ user?.id }}
        </li>
      </ul>

      <button class="btn btn-danger mt-4" @click="logout">
        <i class="bi bi-box-arrow-right"></i> Logout
      </button>
    </div>
  </div>
</template>

<script setup>
import { useAuthStore } from '../stores/auth'
import { useRouter } from 'vue-router'

const auth = useAuthStore()
const router = useRouter()

const user = auth.user

function logout() {
  auth.clearAuth()
  router.push('/login')
}
</script>

<style scoped>
.card {
  background-color: #fff8fb;
}
</style>
