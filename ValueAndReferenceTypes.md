# Tipos por valor e tipos por referência

### Por referência

Definição: tipos passados por referência não são copiados quando atribuídos a variáveis ou passados como argumentos para funções, mas sim sua referência (endereço) na memória é passado. Basicamente um pointer. Se forem feitas alterações nesse dado, elas serão refletidas em todos os lugares em que ele está referenciado.

As variáveis não os contêm. O que fica armazrnado é uma referência / endereço da memória (um pointer).

```
let x = {number: 10}
let y = x;
x.number = 20;
console.log(x.number, y.number) // 20 20
```

**O que entra nessa categoria?**
1. Objetos
2. Funções
3. Arrays

Também é importante lembrar que tipos passados por referência também são comparados por referência, então:

```
const x = {value: 1};
const y = {value: 1};
console.log(x === y) // false
```

Uma forma de verificar se as propriedades e os valores desses objetos são iguais é usar JSON.stringify(obj) nos dois objetos e comparar as strings resultantes.

### Por valor

Definição: tipos passados por valor são **copiados** toda vez que o dado for passado para funções como argumento ou for atribuído a uma variável. Alterações nele não geram mudanças em outras partes do código para as quais ele foi passado.

Tipos primitivos são imutáveis, você não pode alterá-los, apenas substituí-los.

**O que entra nessa categoria?**
1. Number
2. Boolean 
3. String
4. Null
5. Undefined
6. Symbol

```
let x = 10;
let y = x;
x = 20;
console.log(x, y); //20 10
```

x e y são **completamente independentes**
