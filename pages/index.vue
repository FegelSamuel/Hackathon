<script setup lang="ts">
import type { User } from '@/types.d.ts'
import { computed, ref } from 'vue'
import { useRouter } from 'vue-router'

const runtimeConfig = useRuntimeConfig()
console.log(runtimeConfig)

// Access user cookie and authentication state
const user = useCookie<User>('user')
const isLoggedIn = computed(() => user.value?.cuid != null)
const email = ref(user.value?.email)
const role = ref(user.value?.user_role)

// Router for navigation
const router = useRouter()

// Handle Login
const handleLogin = () => {
  // Simulate login logic
  user.value = {
    cuid: '12345', // Example user ID
    email: 'user@example.com',
    user_role: 'admin'
  }
  // Navigate to home page
  router.push('/home')
}
</script>

<template>
  <div>
    <h1>Welcome to the Index Page</h1>
    <!-- Logout Button -->
    <button v-if="isLoggedIn">
      <a href="/api/logout">Logout</a>
    </button>
    <!-- Login Button -->
    <button v-if="!isLoggedIn" @click="handleLogin">
      Login
    </button>
  </div>
</template>
