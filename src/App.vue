<script setup>
import { onMounted } from 'vue'
import { useUserStore } from '@/stores/userStore.js'
import { RouterView } from 'vue-router'
import TheHeader from '@/components/TheHeader.vue'
import Toast from 'primevue/toast'

const authStore = useUserStore()

onMounted(async () => {
  await authStore.getUser()
})
</script>

<template>
  <Toast />
  <TheHeader v-if="authStore.user" />
  <RouterView />
</template>
