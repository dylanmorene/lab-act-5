<template>
  <div class="row justify-content-center">
    <div class="col-md-5">
      <div class="card shadow-sm">
        <div class="card-body">
          <h1 class="h5 mb-3 text-center">Sign In</h1>

          
          <form @submit.prevent="onSubmit">
            <div class="mb-3">
              <label class="form-label">Username</label>
              <input
                v-model="username"
                type="text"
                class="form-control"
                placeholder="kminchelle"
                required
              />
            </div>

            <div class="mb-3">
              <label class="form-label">Password</label>
              <input
                v-model="password"
                type="password"
                class="form-control"
                placeholder="0lelplR"
                required
              />
            </div>

            <button
              class="btn btn-primary w-100"
              type="submit"
              :disabled="loading"
            >
              {{ loading ? 'Logging in...' : 'Login' }}
            </button>

            <p v-if="error" class="text-danger mt-3 text-center">
              {{ error }}
            </p>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter, useRoute } from 'vue-router'
import { useAuthStore } from '../stores/auth'
import { http } from '../api/http'

const username = ref('')
const password = ref('')
const loading = ref(false)
const error = ref('')

const auth = useAuthStore()
const router = useRouter()
const route = useRoute()

async function onSubmit() {
  error.value = ''
  loading.value = true
  try {
    const { data } = await http.post('/auth/login', {
      username: username.value,
      password: password.value
    })
    
    const user = {
      id: data.id,
      username: data.username,
      email: data.email,
      name: `${data.firstName} ${data.lastName}`
    }

   
    auth.setAuth({ token: data.token, user })

  
    router.push(route.query.redirect || '/dashboard')
  } catch (err) {
    error.value = 'Invalid credentials or server error.'
    console.error('Login error:', err)
  } finally {
    loading.value = false
  }
}
</script>
