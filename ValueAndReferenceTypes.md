# Tipos por valor e tipos por referência

### Por referência

Definição: tipos passados por referência não são copiados quando atribuídos a variáveis ou passados como argumentos para funções, mas sim sua referência (endereço) na memória é passado. Basicamente um pointer. Se forem feitas alterações nesse dado, elas serão refletidas em todos os lugares em que ele está referenciado.

**O que entra nessa categoria?**
1. Objetos
2. Funções
3. Arrays

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
