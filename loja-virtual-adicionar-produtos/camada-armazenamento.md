---
title: 'Camada de serviço'
permalink: /loja-virtual-adicionar-produtos/camada-armazenamento
---

# Camada de armazenamento

A camada de armazenamento é responsável por acessar os dados da camada de serviço e disponibilizá-los para os componentes. Ela é responsável por armazenar os dados da aplicação e fazer a comunicação com a camada de serviço. Também, essa camada será responsável por fazer a comunicação com a camada de serviço, bem como manter o gerenciamento de estado da aplicação.

# Camada de armazenamento para categorias

Vamos criar uma camada de armazenamento para categorias. Para isso crie um arquivo chamado `src/stores/category.js` e adicione o seguinte código:

```javascript
import { ref } from 'vue';
import { defineStore } from 'pinia';

import CategoryService from '@/service/category';
const categoryService = new CategoryService();

export const useCategoryStore = defineStore('category', () => {
  const categories = ref([]);

  async function getCategories() {
    categories.value = await categoryService.getCategories();
  }

  async function createCategory(category) {
    await categoryService.createCategory(category);
    getCategories();
  }

  return { categories, getCategories, createCategory };
});
```

Note que criamos dois métodos: `getCategories` e `createCategory`. O método `getCategories` faz uma chamada para a camada de serviço para buscar as categorias cadastradas e armazená-las no estado da aplicação. O método `createCategory` faz uma chamada para a camada de serviço para adicionar uma categoria e, em seguida, chama o método `getCategories` para atualizar a lista de categorias. Também criamos um _ref_ chamado `categories` para armazenar as categorias.

# Camada de armazenamento para uploader de imagens

Vamos criar uma camada de armazenamento para o uploader de imagens. Para isso crie um arquivo chamado `src/stores/uploader.js` e adicione o seguinte código:

```javascript
import { defineStore } from 'pinia';

import UploaderService from '@/service/uploader';
const uploaderService = new UploaderService();

export const useUploaderStore = defineStore('uploader', () => {
  async function uploadImage(image) {
    const { attachment_key } = await uploaderService.uploadImage(image);
    return attachment_key;
  }

  return { uploadImage };
});
```

No código acima, criamos um método `uploadImage` que faz uma chamada para a camada de serviço para fazer o _upload_ de uma imagem e retorna a chave de anexo da imagem.

# Camada de armazenamento para produtos

Nós já temos um serviço para produtos, mas que ainda não tem implementada a criação de produtos. Vamos então adicionar essa funcionalidade. Para isso, edite o arquivo `src/stores/product.js` e substitua o conteúdo pelo seguinte:

```javascript
import { ref } from 'vue';
import { defineStore } from 'pinia';

import ProductService from '@/service/product';
const productService = new ProductService();

export const useProductStore = defineStore('product', () => {
  const products = ref([]);

  async function getProducts() {
    products.value = await productService.getProducts();
  }

  async function getProductsByCategory(category_id) {
    products.value = await productService.getProductByCategory(category_id);
  }

  async function createProduct(product) {
    await productService.createProduct(product);
    getProducts();
  }

  return { products, createProduct, getProducts, getProductsByCategory };
});
```

Nesse caso, criamos três métodos: `getProducts`, `getProductsByCategory` e `createProduct`. O método `getProducts` faz uma chamada para a camada de serviço para buscar os produtos cadastrados e armazená-los no estado da aplicação. O método `getProductsByCategory` faz uma chamada para a camada de serviço para buscar os produtos de uma categoria específica e armazená-los no estado da aplicação. O método `createProduct` faz uma chamada para a camada de serviço para adicionar um produto e, em seguida, chama o método `getProducts` para atualizar a lista de produtos. Também criamos um _ref_ chamado `products` para armazenar os produtos.

Nas próximas etapas, vamos implementar os componentes de criação de produtos e categorias.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Criando a camada de serviço](camada-servico.html 'Voltar')</span><span>[Formulário modal para criação de categorias &gt;](modal-criacao-categorias.html 'Próximo')</span></span>
