---
title: 'Formulário de criação de produtos'
permalink: /loja-virtual-adicionar-produtos/formulario-criacao-produtos
---

# Criando o formulário de criação de produtos

Esse formulário é um pouco mais complexo, pois ele precisa listar as categorias disponíveis para que o usuário possa escolher a categoria do produto. Além disso, o formulário deve permitir o _upload_ de uma imagem para o produto. Também, o formulário deve permitir a adição de novas categorias.

Inicialmente vamos criar o componente do formulário. Para isso, crie um arquivo chamado `src/views/ProductAdd.vue` e adicione o seguinte código:

```vue
<script setup>
import { onMounted, reactive, ref } from 'vue';

import ModalAddCategory from '@/components/ModalAddCategory.vue';
import { useCategoryStore } from '@/stores/category';
import { useProductStore } from '@/stores/product';
import { useUploaderStore } from '@/stores/uploader';

const categoryStore = useCategoryStore();
const productStore = useProductStore();
const uploaderStore = useUploaderStore();

const showModal = ref(false);
const coverUrl = ref('');

const file = ref(null);
const previewImage = ref('');

const product = reactive({
  title: '',
  description: '',
  category: '',
  image_attachment_key: '',
  price: '',
  stock: '',
});

const uploadImage = (e) => {
  file.value = e.target.files[0];
  previewImage.value = URL.createObjectURL(e.target.files[0]);
};

async function save() {
  product.image_attachment_key = await uploaderStore.uploadImage(file.value);
  await productStore.createProduct(product);
  Object.assign(product, {
    title: '',
    description: '',
    category: '',
    image_attachment_key: '',
    price: '',
    stock: '',
  });
}

onMounted(async () => {
  await categoryStore.getCategories();
});
</script>
<template>
  <h1>Adicionar Produto</h1>
  <form class="form" @submit.prevent="save">
    <div class="row-form">
      <label for="title">Título</label>
      <input type="text" id="title" v-model="product.title" />
    </div>
    <div class="row-form">
      <label for="description">Descrição</label>
      <textarea id="description" v-model="product.description"></textarea>
    </div>
    <div class="row-form">
      <label for="category">Categoria</label>
      <div class="row ">
        <select id="category" v-model="product.category">
          <option value="" disabled>Selecione uma categoria</option>
          <option
            v-for="category in categoryStore.categories"
            :key="category.id"
            :value="category.id"
          >
            {{ category.name }}
          </option>
        </select>
        <button class="btn-icon" @click="showModal = !showModal">+</button>
      </div>
    </div>
    <div class="row-form">
      <label for="image">Imagem</label>
      <div class="row">
        <input type="file" id="image" @change="uploadImage" />
        <img
          v-if="previewImage"
          :src="previewImage"
          class="previewImage"
          alt="preview"
        />
      </div>
    </div>
    <div class="row-form">
      <label for="price">Preço</label>
      <input type="number" id="price" v-model="product.price" />
    </div>
    <div class="row-form">
      <label for="stock">Estoque</label>
      <input type="number" id="stock" v-model="product.stock" />
    </div>
    <button class="btn-send" type="submit">Adicionar</button>
  </form>
  {{ product }} - {{ coverUrl }} - {{ previewImage }} - {{ file }}

  <modal-add-category v-if="showModal" @close="showModal = !showModal" />
</template>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 2rem;
  margin-left: 2rem;
}

.row-form {
  display: flex;
  flex-direction: column;
  font-size: 1.3rem;
  max-width: 400px;
}

.form button.btn-send {
  background-color: #0a2668;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 1rem;
  font-size: 1.3rem;
  cursor: pointer;
  width: 200px;
}

.form button.btn-icon {
  background-color: #0a2668;
  color: white;
  border: none;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin-left: 0.3rem;
  font-size: 1rem;
  cursor: pointer;
}

.previewImage {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border-radius: 50%;
  border: 4px solid #0a2668;
  padding: 0.1rem;
}
</style>
```

No código acima, criamos um formulário para adicionar produtos. O formulário é composto por campos para o título, descrição, categoria, imagem, preço e estoque do produto. O campo de categoria é um _select_ que lista as categorias disponíveis. O formulário possui um botão para adicionar o produto.

Vou detalhar cada um dos três blocos do código

## Script setup

No bloco de script, importamos as funções necessárias para a criação do componente. Importamos os _stores_ de categoria, produto e _uploader_. Também importamos o componente `ModalAddCategory`. Criamos as variáveis reativas necessárias para o formulário e para o _upload_ da imagem. Criamos a função `uploadImage` para fazer o _upload_ da imagem. Criamos a função `save` para salvar o produto. Por fim, chamamos a função `getCategories` para buscar as categorias disponíveis.

Note que a função `uploadImage` armazena a imagem em uma variável `file` e cria uma URL para a imagem em uma variável `previewImage`. A função `save` faz o _upload_ da imagem e, em seguida, chama a função `createProduct` para adicionar o produto.

## Template

No bloco de template, criamos o formulário para adicionar produtos. O formulário possui campos para o título, descrição, categoria, imagem, preço e estoque do produto. O campo de categoria é um _select_ que lista as categorias disponíveis. O formulário possui um botão para adicionar o produto.

Note que o campo _select_ de categoria lista as categorias disponíveis no _store_ de categorias. O botão `+` ao lado do campo de categoria abre o modal para adicionar uma nova categoria.

## Estilização

No bloco de estilização, definimos o estilo do formulário. O formulário é exibido em colunas e possui um espaçamento entre os campos. O botão de envio do formulário possui um estilo azul e um espaçamento interno. O botão `+` ao lado do campo de categoria possui um estilo azul e um formato redondo. A imagem do preview da imagem possui um tamanho fixo e um estilo de borda.

Para finalizar, faremos alguns ajustes na tela de listagem de produtos para que o usuário possa navegar para a tela de adição de produtos.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Modal para criação de categorias](modal-criacao-categorias.html 'Voltar')</span><span>[Ajustes na listagem de produtos &gt;](ajustes-listagem-produtos.html 'Próximo')</span></span>
