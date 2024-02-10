<script setup>
import { useRegisterSW } from 'virtual:pwa-register/vue';
const { isUpdateAvailable, updateServiceWorker } = useRegisterSW();

const update = async () => {
  await updateServiceWorker();
  window.location.reload();
};
</script>

<template>
  <div v-if="isUpdateAvailable" class="install-app">
    <button @click="update">Atualizar aplicação</button>
  </div>
</template>
