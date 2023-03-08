---
title: "Props"
permalink: /recursos/pros
---

# Props

Neste tópico vamos conhecer o recurso `props` do React Native. Este recurso é usado para passar dados de um componente pai para um componente filho.

Para exemplificar o uso de `props`, vamos dar continuidade ao exemplo do contador. No exemplo anterior, o componente `Contador` foi criado como um componente de classe. Agora, vamos colocar um limite para o contador. O contador não pode ser incrementado se o valor for maior que um limite que será informado via `props`.

Nesse caso, inicialmente vamos alterar a chamada do componente `Contador` no arquivo `src/App.js`:

```jsx
import React from 'react'
import { View } from 'react-native'
import Contador from './src/components/Contador'

export default function App() {
  return (
    <View>
      <Contador limite={10} />
    </View>
  )
}
```

Note que o componente `Contador` recebe uma propriedade chamada `limite` com o valor `10`. Esta propriedade pode ser acessada através da propriedade `this.props` do componente.

Agora, vamos alterar o componente `Contador` para usar a propriedade `limite`:

```jsx
import React, { Component } from 'react'
import { View, Text, Button } from 'react-native'

export default class Contador extends Component {

  state = {
    contador: 0
  }

  incrementar = () => {
    if (this.state.contador < this.props.limite) {
      this.setState({ contador: this.state.contador + 1 })
    }
  }

  render() {
    return (
      <View>
        <Text>Contador</Text>
        <Text>{this.state.contador}</Text>
        <Button title="Incrementar" onPress={this.incrementar} />
      </View>
    )
  }
}
```

Veja que o componente `Contador` foi alterado para usar a propriedade `limite` através da propriedade `this.props.limite`. O método `incrementar` foi alterado para verificar se o contador é menor que o limite antes de incrementar o contador.

<span style="display: flex; justify-content: space-between;"><span>[&lt; State](state.html "Voltar")</span> <span>[Style &gt;](style.html "Próximo")</span></span>