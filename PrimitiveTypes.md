
# Tipos primitivos

Definição: tipos que são **passados por valor** (copiados) e **armazenados na call stack** (elementos ficam um em cima do outro)

### Quais são?
1. String
2. Number
3. Boolean
4. Undefined
5. Null
6. Symbol

```
let cinco = 5;
let outroCinco = cinco; // cinco e outroCinco são cincos diferentes. O valor da variável **cinco** foi **integralmente copiado** para **outroCinco**
```

# Tipos não primitivos

Definição: são os **objetos**. Armazenam mais de um dado e mais de um tipo de dado e são **passados por referência** (pointers / endereços).
Seu armazenamento é foi no **memory heap** (elementos não têm uma ordem específica defolxs distribuição).

Lembre-se que funções e arrays também são objetos.

```
let pessoa = { 'name': 'gabriel' };
let mesmaPessoa = pessoa; // pessoa e mesmaPessoa guardam a mesma referência na memória (o mesmo pointer), logo são a mesma coisa.
```
