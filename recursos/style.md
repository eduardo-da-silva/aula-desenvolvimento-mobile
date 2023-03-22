---
title: "Style"
permalink: /recursos/style
---

# Estilos em React Native

O React Native usa o CSS para estilizar os componentes, mas não o CSS padrão. Em vez disso, o React Native usa um conjunto de propriedades CSS que são mapeadas para as propriedades nativas do dispositivo. Na prática, não se aplica diretamente o CSS padrão, mas uma notação similar ao ao CSS, que o React Native suporta. Por exemplo, o CSS padrão usa `background-color` para definir a cor de fundo de um elemento, enquanto o React Native usa `backgroundColor` .

## Estilos em geral

Em geral, os componentes React Native possuem uma propriedade `style` que aceita um objeto JavaScript com estilos. Por exemplo, para definir a cor de fundo de um componente `View` , você pode usar:

```jsx
<View style={% raw %} {{ backgroundColor: 'blue' }} {% endraw %}/>
```

Nesse exemplo, o objeto JavaScript contém uma propriedade `backgroundColor` com o valor `blue` . O React Native mapeia essa propriedade para a propriedade nativa `backgroundColor` do componente `View`.

É possível também definir estilos em um objeto separado e passá-lo para o componente. Por exemplo:

```jsx
<View style={styles.container} />

...

const styles = StyleSheet.create({
  container: {
    backgroundColor: 'blue',
  },
});
```

Nesse exemplo, o objeto `styles` contém uma propriedade `container` com o valor `{ backgroundColor: 'blue' }` . O React Native mapeia essa propriedade para a propriedade nativa `backgroundColor` do componente `View`.

    Note que na medida em que a complexidade dos componentes aumenta, é mais fácil manter os estilos em um objeto `StyleSheet.create` separado.


## Layouts com Flexbox

O React Native usa o Flexbox para definir layouts. O Flexbox é um sistema de layout unidimensional que define como os itens são distribuídos em uma linha ou coluna. O Flexbox é baseado em três conceitos principais: o eixo principal, o eixo transversal e o alinhamento. O eixo principal é a direção em que os itens são distribuídos. O eixo transversal é a direção perpendicular ao eixo principal. O alinhamento é a forma como os itens são distribuídos ao longo do eixo principal.

Em geral, usa-se uma combinação das propriedades `flexDirection` , `justifyContent` e `alignItems` para definir o layout de um componente. A propriedade `flexDirection` define o eixo principal, a propriedade `justifyContent` define o alinhamento ao longo do eixo principal e a propriedade `alignItems` define o alinhamento ao longo do eixo transversal.

Mais informações de uso podem ser encontradas na [documentação do React Native](https://reactnative.dev/docs/flexbox "Flexbox").

<span style="display: flex; justify-content: space-between;"><span>[&lt; Props](props.html "Voltar")</span> <span>[Imagens &gt;](imagens.html "Próximo")</span></span>