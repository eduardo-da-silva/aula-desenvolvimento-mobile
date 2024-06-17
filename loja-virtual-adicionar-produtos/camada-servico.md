---
title: 'Camada de serviço'
permalink: /loja-virtual-adicionar-produtos/camada-servico
---

# Camada de serviços

Vamos, inicialmente, criar as funções da camada de serviço, que fará a comunicação com a API do _backend_. Essa camada será posteriormente acessada pela camada de armazenamento, embora possa ser acessada diretamente dos componentes.

# Camada de serviço para categorias

Vamos criar uma camada de serviço para categorias. Essa camada será responsável por fazer a comunicação com a API do _backend_ para buscar e adicionar categorias. Para isso crie um arquivo chamado `src/services/category.js` e adicione o seguinte código:

```javascript
import axios from 'axios';

export default class CategoryService {
  async getCategories() {
    const response = await axios.get('/categories/');
    return response.data.results;
  }

  async createCategory(category) {
    const response = await axios.post('/categories/', category);
    return response.data;
  }
}
```

Note que criamos dois métodos: `getCategories` e `createCategory`. O método `getCategories` faz uma chamada GET para a URL `/categories/` e retorna as categorias cadastradas. O método `createCategory` faz uma chamada POST para a URL `/categories/` com a categoria a ser cadastrada.

# Camada de serviço para produtos

Nós já temos um serviço para produtos, mas que ainda não tem implementada a criação de produtos. Vamos então adicionar essa funcionalidade. Para isso, edite o arquivo `src/services/product.js` e substitua o conteúdo pelo seguinte:

```javascript
import axios from 'axios';

export default class ProductService {
  async getProducts() {
    const response = await axios.get('/products/');
    return response.data.results;
  }

  async getProductByCategory(category_id) {
    const response = await axios.get(`/products/?category__id=${category_id}`);
    return response.data.results;
  }

  async createProduct(product) {
    const response = await axios.post('/products/', product);
    return response.data;
  }
}
```

Agora, temos o método `createProduct` que faz uma chamada POST para a URL `/products/` com o produto a ser cadastrado.

Na próxima etapa, vamos implementar a camada de armazenamento para acessar esses métodos.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Tutorial da loja virtual - adicionar produtos](. 'Voltar')</span><span>[Criando a camada de armazenamento &gt;](camada-armazenamento.html 'Próximo')</span></span>
