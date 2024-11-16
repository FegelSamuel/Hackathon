<script setup lang="ts">
  import type { User } from '@/types.d.ts'
  import { computed, ref } from 'vue'
  const runtimeConfig = useRuntimeConfig()
  console.log(runtimeConfig)

const user = useCookie<User>('user');
const isLoggedIn = computed(() => (user.value?.cuid != null)) // linter is mad here, don't worry about it
const email = ref(user.value?.email)
const role = ref(user.value?.user_role)
</script>

<template>
<div>
  <button v-if="isLoggedIn"></button>
    <a href="/api/logout"> Logout </a>
  <button v-if="!isLoggedIn"></button>
    <a href="/api/login"> Login </a>
</div>
</template>
