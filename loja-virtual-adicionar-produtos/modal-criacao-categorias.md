---
title: 'Modal de criação de categorias'
permalink: /loja-virtual-adicionar-produtos/modal-criacao-categorias
---

# Criando o modal de criação de categorias

No nosso projeto, teremos uma opção para adicionar novas categorias a partir do formulário de criação de produtos. Para isso, vamos criar essa funcionalidade em um modal. Vale lembrar que o modal é um componente que fica sobreposto à tela e é utilizado para exibir informações adicionais ou para realizar ações específicas.

Inicialmente vamos criar o componente do modal. Para isso, crie um arquivo chamado `src/components/ModalAddCategory.vue` e adicione o seguinte código:

```vue
<script setup>
import { reactive, defineEmits } from 'vue';
import { useCategoryStore } from '@/stores/category';

const emit = defineEmits(['close']);

const categoryStore = useCategoryStore();

const category = reactive({
  name: '',
  icon: '',
});

const createCategory = async () => {
  await categoryStore.createCategory(category);
  emit('close');
};
</script>

<template>
  <div class="modal">
    <div class="modal-content">
      <div class="modal-header">
        <h2>Adicionar Categoria</h2>
        <button @click="$emit('close')" class="btn-close">
          <i class="mdi mdi-close" />
        </button>
      </div>
      <form class="form" @submit.prevent="createCategory">
        <div class="row-form">
          <label for="name">Nome</label>
          <input type="text" id="name" v-model="category.name" />
        </div>
        <div class="row-form">
          <label for="icon">Ícone</label>
          <input type="text" id="icon" v-model="category.icon" />
        </div>
        <button class="btn-send" type="submit">Adicionar</button>
      </form>
    </div>
  </div>
</template>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 100;
}

.modal-content {
  background-color: white;
  padding: 2rem;
  border-radius: 10px;
  width: 30%;
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.modal-header h2 {
  font-size: 1.5rem;
}

.btn-close {
  background-color: #0a2668;
  color: white;
  border: none;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  cursor: pointer;
}

.btn-close i {
  font-size: 1.5rem;
}

.form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.row-form {
  display: flex;
  flex-direction: column;
  font-size: 1.3rem;
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
</style>
```

No código acima, criamos um modal para adicionar categorias. O modal é composto por um formulário com os campos `name` e `icon`. O campo `name` é obrigatório e o campo `icon` é opcional. O modal possui um botão para fechar o modal e um botão para adicionar a categoria.

Vou detalhar cada um dos três blocos do código:

1. **Script setup**: Neste bloco, importamos as funções `reactive` e `defineEmits` do Vue. Também importamos o _store_ de categorias e definimos a função `createCategory` para adicionar uma categoria. Além disso, definimos a função `emit` para emitir o evento `close` quando o modal for fechado. Esse evento será capturado pelo componente pai para fechar o modal.

2. **Template**: Neste bloco, criamos o conteúdo do modal. O modal é composto por um cabeçalho com o título "Adicionar Categoria", um botão para fechar o modal e um formulário com os campos `name` e `icon`. O formulário possui um botão para adicionar a categoria. Foram também definidas as classes CSS para estilizar o modal.

3. **Estilos**: Neste bloco, definimos os estilos do modal. O modal é posicionado no centro da tela e possui um fundo escuro. O conteúdo do modal possui um fundo branco e um espaçamento interno de 2rem. O cabeçalho do modal possui um espaçamento inferior de 1rem e os campos do formulário possuem um espaçamento de 1rem. O botão de fechar o modal possui um fundo azul escuro e o botão de adicionar a categoria possui um fundo azul escuro e um espaçamento interno de 1rem.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Criando a camada de armazenamento](camada-armazenamento.html 'Voltar')</span><span>[Formulário para criação de produtos &gt;](formulario-criacao-produtos.html 'Próximo')</span></span>
