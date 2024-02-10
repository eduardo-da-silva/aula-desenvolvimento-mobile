<script setup>
import axios from 'axios';
import { ref, onMounted } from 'vue';

const products = ref([]);

onMounted(async () => {
  const resp = await axios.get('https://fakestoreapi.com/products');
  products.value = resp.data;
});
</script>

<template>
  <main>
    <h1>Meninos da Ayrton Senna</h1>
    <hr />
    <div class="items" v-for="product in products" :key="product.id">
      {{ product.title }} - {{ product.price }}
      <img class="img-item" :src="product.image" :alt="product.title" />
      <hr />
    </div>
  </main>
</template>

<style scoped>
.items {
  margin: 1rem 0;
  padding: 1rem;
  border: 1px solid var(--color-border);
  border-radius: 4px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  transition: box-shadow 0.3s ease;
}
.img-item {
  max-width: 100px;
  margin: 1rem 0;
}
</style>
