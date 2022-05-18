# Tipos por valor e tipos por referência

### Por referência

Definição: tipos passados por referência não são copiados quando atribuídos a variáveis ou passados como argumentos para funções, mas sim sua referência (endereço) na memória é passado (basicamente como se fosse a **criação de um apelido... uma pessoa com um apelido ainda é a mesma pessoa**). Basicamente um pointer. Se forem feitas alterações nesse dado, elas serão refletidas em todos os lugares em que ele está referenciado.

As variáveis não os contêm. O que fica armazrnado é uma referência / endereço da memória (um pointer).

São **armazenados na MEMORY HEAP**

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

Definição: tipos passados por valor são **copiados** toda vez que o dado for passado para funções como argumento ou for atribuído a uma variável. Alterações nele não geram mudanças em outras partes do código para as quais ele foi passado (exemplo dos **irmãos gêmeos: um nçao fica sem perna quando o outro perde a sua na guerra (wtf kkkkk)**

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

- Os tipos primitivos possuem um **objeto "em volta deles" (object wrapper)**. Isso acontece devido a um mecanismo do JS chamado **auto-boxing**. Por trás dos panos, um **objeto temporário é criado em volta do tipo primitivo** quando ele é tratado como um objeto.

- São **armazenados na CALL STACK (assim como as referências par objetos)**

# Por que existe essa diferença?

- Razões de **performance**! Copiar um valor primitivo não é muito custoso em termos de processamento, pois tipos primitivos se referem a apenas um dado. Já com objetos é diferente, visto que eles podem vir a ser grandes e complexos, e copiá-los poderia ser custoso e ineficiente.

# Funções puras

Definição: são funções que **não afetam nada fora do seu escopo (não mudam variáveis de fora nem objetos)**. Todas as variáveis presentes em uma função pura sofrem **garbage collection** assim que a função termina sua execução. Uma função que recebe um objeto como parâmetro e faz alterações diretamente nesse objeto (sem fazer uma cópia dele) é uma **função impura**

**Exemplos:** filter, map, reduce
