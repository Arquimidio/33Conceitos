
# Tipos primitivos

Definição: tipos que são **passados por valor** (copiados) e **armazenados na call stack** (elementos ficam um em cima do outro)

Primitivo significa **básico**

### Quais são?
1. String (cadeias de caracteres)
2. Number (floats e ints são do mesmo data type)
3. Boolean
4. Undefined
5. Null
6. NaN
7. Symbol

```
let cinco = 5;
let outroCinco = cinco; // cinco e outroCinco são cincos diferentes. O valor da variável **cinco** foi **integralmente copiado** para **outroCinco**

```
### null e undefined

null = inexistência por vontade do programador (ausência de valor)
undefined = ausência de definição geralmente resultado de alguma operação no programa

### Resumo
1. Tipos primitivos são **imutáveis**
2. Tipos primitivos são **passados e também comparados por valor**

# Tipos não primitivos

Definição: são os **objetos**. Armazenam mais de um dado e mais de um tipo de dado e são **passados por referência** (pointers / endereços).
Seu armazenamento é foi no **memory heap** (elementos não têm uma ordem específica defolxs distribuição).

Lembre-se que funções e arrays também são objetos.

```
let pessoa = { 'name': 'gabriel' };
let mesmaPessoa = pessoa; // pessoa e mesmaPessoa guardam a mesma referência na memória (o mesmo pointer), logo são a mesma coisa.
```

### Copiando um objeto
Uma maneira básica de copiar um objeto é utilizando Object.assign({}, objetoASerCopiado) **shallow copy (só a primeira camada de profundidade)**

**array.slice()** sem argumentos pode ser usado para também fazer uma **shallow copy**

# Variáveis

Definição: uma variável é basicamente um container para dados. É convencional usar camelCase no nome de variáveis, e é regra não usar caracteres especiais (exceto $ e _) e não iniciá-las com digitos

# Sobre o heap e a stack

Call Stack = armazena **value types** (tipos primitivos)
Memory Heap = armazena **reference types** (objetos) 

# Entendendo Numbers

### Como são registrados na memória?

