<script setup lang="ts">
import { useRouter } from 'vue-router'
import { useCookie } from '#app'

// Router for navigation
const router = useRouter()

// Access user cookie
const user = useCookie('user')

// Handle Logout
const handleLogout = () => {
  // Simulate clearing user session
  user.value = null
  // Navigate to index page
  router.push('/')
}
</script>

<template>
  <div>
    <h1>Welcome to the Home Page</h1>
    <!-- Logout Button -->
    <button @click="handleLogout">Logout</button>
  </div>
</template>
