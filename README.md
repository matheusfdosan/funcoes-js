# Funções

Uma função é um bloco de comandos, que pode ser executada em um momento oportuno, ou seja, posso utilizar em um momento que sua execução for necessária.

## Declarando funções

Primeiramente, escrevemos a palavra-chave **function**, depois adicionamos um nome seguido de parentese (normalmente, damos os nomes para as funções com relação a sua utilidade). E dentro dos parênteses, vão ficar um conjunto de parâmetros, que são

E por fim, abrimos e fechamos chaves, e dentro dessas chaves, irão ficar nosso bloco de código.

```js
function showName() {
  const name = "Matheus Faustino"
  console.log(name)
}

showName() // Esse código executa a função

// Output: Matheus Faustino
```

## Return

As funções nem sempre precisam executar ações no programa, como braços e pernas. As funções também podem ser como um cérebro e fazer cálculos complexos e retornar valores.

Logo, para retornar valores, utilizamos o comando **return**:

```js
function somar2_2() {
  return 2 + 2
}

console.log(somar2_2())
```

Essa função retorna o valor 4.

> Vale ressaltar que, qualquer código escrito depois do comando return não funcionará:

```js
function parOuÍmpar() {
  let number = 21

  if (number % 2 === 0) {
    return "Par"
  }

  return "Ímpar"
}

console.log(parOuÍmpar())
```

Temos aqui um exemplo prático do comando "return". Sabendo que, nenhum código irá funcionar depois do primeiro retorno da função, se o resto da divisão do **number** for igual a 0, ou seja, se for par, a função retornará "Par", e finalizará. Mas se não for par, o código prosseguirá, e retornará ímpar.

## Utilizando parâmetros

Os parâmetros, são valores que são passados na hora da execução da função, mais especificadamente, dentro dos parênteses. Contudo, usamos esses valores como variáveis na declaração da função, e que só vão funcionar dentro do escopo da função:

```js
function soma(n1, n2) {
  return n1 + n2
}

console.log(soma(10, 30))
```

Suponhamos que, temos uma função que precisa de 2 parâmetros para funcionar, mas em sua chamada, tem apenas um valor. Para resolver isso podemos adicionar um valor padrão para os parâmetros:

```js
const PADRAO = 0

function multiplicação(num1 = PADRAO, num2 = PADRAO) {
  return num1 * num2
}

console.log(multiplicação(5))
// Agora se faltar algum valor, a função retornará sempre 0
```

## Parâmetros REST

O parâmetro REST, é um método que percorre um array, pegando seus valores, e ordenando conforme a quantidade de parâmetros na função, veja:

```js
function texoApresentativo(nome, idade, coisaFavorita) {
  return `Oi, me chamo ${nome}, tenho ${idade} anos de idade, e a minha coisa favorita é ${coisaFavorita}.`
}

const pessoa = ["Matheus Faustino", 15, "Comer Pizza"]

console.log(texoApresentativo(...pessoa))

// Output: Oi, me chamo Matheus Faustino, tenho 15 anos de idade, e a minha coisa favorita é Comer Pizza.
```

## Funções anônimas

As funções anônimas são funções que não possuem uma identidade, um nome associado ao seu conteúdo. Ela é colocada em uma variável, logo, a variável assume uma associação direta com a função anônima, e a função é executada colocando o nome da variável seguido de abre e fecha parenteses:

```js
const soma = (...valores) => {
  let res = 0

  for (let valor of valores) {
    res += valor
  }

  return res
}

console.log(soma(50, 15, 20, 30))
// Output: 115
```

### Função Construtor anônima

Quando falamos de construtor ou de classes, sempre utilizamos um operador chamado **new**, que muda a construção de nossa função. Usamos esse método na criação de funções mais simples, como, por exemplo, uma função que recebe 2 parâmetros, e faz uma operação simples de retorno:

```js
const soma = new Function("n1", "n2", "return n1 + n2")

console.log(soma(10, 10))
// Output: 20
```

## Arrow Function

Arrow Function é uma sintaxe mais curta para escrever funções em JavaScript. Seu nome é por conta de uma característica da forma que é declarada, utilizando-se uma seta (=>).

```js
const multiplicação = (...valores) => {
  let iterador = 1
  for (let valor of valores) {
    iterador *= valor
  }
  return iterador
}

console.log(multiplicação(3, 3, 5))
// Output: 45
```

Caso tenha apenas um parâmetro, não é necessário colocar entre parenteses, colocamos o nome do parâmetro é pronto. E se não tiver nenhum parâmetro, podemos colocar apenas os parenteses ou underscore. E se o código dentro da função tiver apenas uma linha, não é preciso colocar entre chaves, e nem escrever o comando **return**:

```js
const message = (_) => "Hello, World!"

console.log(message())
// Output: Hello, World!
```

## Funções aninhadas / internas

Basicamente, é uma função dentro da outra. São utilizadas quando precisamos executar uma tarefa específica em uma função.

> Isso deixa o escopo do código mais organizado e limitado, evitando erros com outras partes do código.

```js
const soma = (...valores) => {
  const somar = (arrayValores) => {
    let resultado = 0
    for (let valor of arrayValores) {
      resultado += valor
    }
    return resultado
  }

  return somar(valores)
}

const array = [12, 34, 89]
console.log(soma(...array))
```

Neste exemplo, a função externa `soma` contém uma função interna `somar`. A função `somar` só pode ser acessada dentro da função `soma`, porque está dentro do escopo da função externa. Quando a função externa é chamada, contendo valores para serem somados, ela executa a função interna `somar`, que vai pegar os valores do parâmetro e retornará o resultado final e, em seguida, chama a função externa irá retornar o retorno da função externa.

## Funções Geradoras

As funções geradoras são funções que geram um fluxo de valores sob demanda, ou seja, uma sequência de valores que podem ser consumidos ao longo do tempo.

Com a função geradora, a própria função tem o controle de quando ela quiser retornar alguma coisa. Então, basicamente, quando chamo uma função normal, é necessário um processamento voltado para retornar uma única coisa no final. Logo, com a função geradora, posso ir retornando coisas ao longo do programa, ou seja, é uma maneira de criar sequências de valores que podem ser retornados um por vez, conforme necessário.

### Criando uma função geradora

Para criar uma função geradora, você deve usar a palavra-chave `function*` em vez de `function` na declaração da função. 

Ela é uma função que cria uma sequência de valores que podem ser retornados um por vez, e para fazer essa sequência de valores, ela irá retornar sempre que tiver um `yield`, ou seja, a palavra-chave `yield` pausa a execução da função e retornar um valor.

```js
function* cores() {
  yield "red"
  yield "green"
  yield "blue"
}

// Primeira vez da chamada da função, retorna um iterator
const itc = cores()
// itc = iterator da função cores()

// Segunda vez da chamada da função, irá entrar em sua execução, e irá retornar sempre que tiver um `yield`
console.log(itc.next().value)
console.log(itc.next().value)
// Pego o valor do próximo retorno (do próximo yield)
console.log(itc.next().value)
// A cada execução da função, depois do iterator, retorna um valor do yield por vez
```

### E se as chamadas passarem do limite?

Agora, se as chamadas das funções passarem do limite, as chamadas seguintes retornarão `undefined`, indicando não haver mais valores a serem consumidos. Mas podemos reiniciar o iterador, por meio da atribuição itc = cores(). Isso cria um novo iterador para a função cores(), que agora pode ser percorrido novamente:

```js
function* cores() {
  yield 'amarelo'
  yield 'laranja'
  yield 'roxo'
}

let itc = cores()
console.log(itc.next().value)
console.log(itc.next().value)
console.log(itc.next().value)
console.log(itc.next().value) // undefined

itc = cores() // reiniciar o iterador
console.log(itc.next().value)
console.log(itc.next().value)
console.log(itc.next().value)
```

### "Interagir" com o usuário

```js
function* perguntas() {
  const nome = yield "Qual seu nome?"
  const idade = yield "Qual sua idade?"
  return `Seu nome é ${nome}, e você tem ${idade} anos!`
}

const itp = perguntas()
console.log(itp.next().value)
console.log(itp.next("Matheus").value)
console.log(itp.next(15).value)
```

Na primeira chamada, é impressa a primeira pergunta, que solicita o nome do usuário. Na segunda chamada, é passado o valor "Matheus" como argumento para o método next(), recebido como o valor da variável nome.

Em seguida, é impressa a segunda string gerada pela função, que solicita a idade do usuário. Na terceira chamada, é passado o valor 15 como argumento para o método next(), que é recebido como o valor da variável idade.

Por fim, é retornada a string que combina as informações do usuário em uma única frase.

### Exemplo de uso: Contador de 0 a 10

```js
function* contador() {
  let num = 0
  while (true) { // loop infinito
    yield num++

    if (num > 10) {
      break
      // quando o num for maior que 10: para o loop
    }
  }
}

const itc = contador()

for (let number of itc) {
  console.log(number)
} // cada número gerado pela função é atribuído à variável number, que é então impressa no console.
```

