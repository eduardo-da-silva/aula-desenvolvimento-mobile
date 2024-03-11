<script setup>
import { useScreen } from '@/composables/screen';

const { menu } = useScreen();
</script>

<template>
  <div>
    <component :is="menu" />
    <main>
      <router-view />
    </main>
    <footer>
      <p>Copyright &copy; 2023</p>
    </footer>
  </div>
</template>
