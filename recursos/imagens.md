---
title: "Imagens"
permalink: /recursos/imagens
---

# Imagens

O React Native suporta a maioria dos formatos de imagem, incluindo PNG, JPG, GIF e SVG. Para usar uma imagem, você deve importá-la usando o `require` e usar em conjunto com o component `Image` . Por exemplo:

```jsx
import { Image } from 'react-native';
const logo = require('./logo.png');

...

<Image source={logo} style={%raw}{{ width: 305, height: 159 }}{%endraw} />
```
Nesse exemplo, o objeto `logo` contém o caminho para a imagem. O React Native mapeia essa propriedade para a propriedade nativa `source` do componente `Image`. Também foi definido o tamanho da imagem usando as propriedades `width` e `height` .

Também podem ser utilizadas imagens que não estão armazenadas localmente. Por exemplo, para usar uma imagem de um servidor remoto, você pode usar:

```jsx
import { Image } from 'react-native';

...

<Image
  source={% raw %}{{
    uri: 'https://reactnative.dev/img/tiny_logo.png'}}
  style={{
    width: 64,
    height: 64,
  }}{% endraw %}
/>
```

Nesse caso, o objeto `source` contém o caminho para a imagem e o tamanho da imagem, definido pela propriedade `uri`.

Mais informações de uso podem ser encontradas na [documentação do React Native](https://reactnative.dev/docs/images "Imagens").


<span style="display: flex; justify-content: space-between;"><span>[&lt; Style](style.html "Voltar")</span> <span>[Exercícios &gt;](exercicios.html "Próximo")</span></span>