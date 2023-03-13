---
title: "State"
permalink: /recursos/state
---

# State

O `state` é usado para armazenar dados que podem ser alterados durante a execução do aplicativo. Ele é um objeto que pode ser acessado através da propriedade `this.state` de um componente. Nós abordaremos neste tópico o uso de `state` em componentes de classe.

Para exemplificar o uso de `state`, vamos criar um componente que exibe um contador. O contador será incrementado a cada clique no botão.

Em primeiro lugar, vamos criar um componente de classe que exibe o contador. Este componente pode estar no arquivo `src/components/Contador.js`:

```jsx
import React, { Component } from 'react'
import { View, Text, Button } from 'react-native'

export default class Contador extends Component {
  render() {
    return (
      <View>
        <Text>Contador</Text>
        <Button title="Incrementar" onPress={() => {}} />
      </View>
    )
  }
}
```

No exemplo acima, o componente `Contador` possui um botão que não faz nada. Vamos incrementar o contador a cada clique no botão.

Para isso, vamos criar um `state` para o componente `Contador`. O `state` é um objeto que pode ser acessado através da propriedade `this.state` de um componente. O `state` é inicializado no construtor do componente:

```jsx
import React, { Component } from 'react'
import { View, Text, Button } from 'react-native'

export default class Contador extends Component {

  state = {
    contador: 0
  }

  incrementar() {
    this.setState({ contador: this.state.contador + 1 })
  }

  render() {
    return (
      <View>
        <Text>Contador</Text>
        <Button title="Incrementar" onPress={() => {}} />
      </View>
    )
  }
}
```

Note que o `state` é inicializado com o valor `0` para a propriedade `contador`. O método `incrementar` é responsável por incrementar o contador. Ele faz isso através da chamada do método `setState` do componente. O método `setState` recebe um objeto com as propriedades que devem ser alteradas no `state`. No exemplo acima, o `state` é alterado para incrementar o valor da propriedade `contador` em `1`.

Agora, vamos usar o método `incrementar` no evento `onPress` do botão:

```jsx
import React, { Component } from 'react'
import { View, Text, Button } from 'react-native'

export default class Contador extends Component {

  state = {
    contador: 0
  }

  incrementar() {
    this.setState({ contador: this.state.contador + 1 })
  }

  render() {
    return (
      <View>
        <Text>Contador</Text>
        <Button title="Incrementar" onPress={() => this.incrementar()} />
      </View>
    )
  }
}
```

Para finalizar, vamos exibir o valor do contador no componente:

```jsx
import React, { Component } from 'react'
import { View, Text, Button } from 'react-native'

export default class Contador extends Component {

  state = {
    contador: 0
  }

  incrementar() {
    this.setState({ contador: this.state.contador + 1 })
  }

  render() {
    return (
      <View>
        <Text>Contador: {this.state.contador}</Text>
        <Button title="Incrementar" onPress={() => this.incrementar()} />
      </View>
    )
  }
}
```

Por fim, vamos usar o componente `Contador` no arquivo `src/App.js`:

```jsx
import React from 'react'
import { View } from 'react-native'
import Contador from './src/components/Contador'

export default function App() {
  return (
    <View>
      <Contador />
    </View>
  )
}
```

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](. "Voltar")</span> <span>[Props &gt;](props.html "Próximo")</span></span>