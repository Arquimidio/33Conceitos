# Tipos de conversão

- A conversão pode ser realizada para 3 tipos diferentes
1. String (strings convertidas para números e que tem apenas caracteres de espaço resultam em 0 em vez de NaN)
2. Number (implícita com operadores de comparação (>=, <, etc), bitwise, aritméticos e igualdade simples (== e !=)
3. Boolean (implícita em contextos lógicos e com os operadores !, || &&)

- A lógica de conversão **funciona de forma diferente para PRIMITIVOS e OBJETOS**

# Coerção implícita

definição: É o processo de conversão de um valor de um tipo para outro. Tentativa do JavaScript de converter um **valor de tipo inesperado** para um do **tipo esperado** (a liguagem "tenta advinhar" que tipo de operação o programador pretendia realizar). Acontece em operações (+, -, ==, etc) e também em determinados contextos (if(something)...)

Obs1: isso acontece porque **JavaScript é uma linguagem fracamente tipada**

Obs2: o operador **===** **NÃO REALIZA COERÇÃO IMPLÍCITA**

Obs3: symbols só podem sofrer coerção para string se ela for **explícita**

Obs4: **null em number é 0** e **undefined em number é NaN**

### Regras a serem lembradas

1. null == null (true) e null == undefined (true)
2. NaN == NaN (false) (NaN não é igual a outro NaN)

**EVITE SEMPRE QUE POSSÍVEL A COERÇÃO IMPLÍCITA**

### Valores **não numéricos** em **expressões numéricas**
1. **Strings**: se (*, -, /, %) resulta em **conversão em Number**, já se (+) resulta em **concatenação**. Se a string contiver **caracteres não numéricos**, resulta em **NaN**
2. **Objetos**: a maioria das conversões de objetos resulta na string **[object Object]**. Isso porque o método **toString** do objeto é utilizado nessas operações de conversão (essa função pode ser **sobrecrita dentro do objeto para alterar esse comportamento**)
3. **Arrays**: a conversão de arrays também é baseada no método **toString**, mas ele funciona como um join(). Os valores do array serão juntados em uma string e separados por **vírgulas**. Daí em diante, as operações ocorrem da mesma forma que com strings
4. **true, false e ''**: true vira **1** e false e '' viram **0*
5. **valueOf**: é possível definir um método **valueOf** nos objetos. Se ele estiver definido, terá **preferência sobre o toString**. Esse método **geralmente é usado para objetos que devem representar um valor numérico**


### Truthy e Falsy

definição: **qualquer valor** pode ser **convertido para seu equivalente booleano (true ou false)**

- Os valores **Falsy** são:

1. 0
2. ''
3. NaN
4. undefined
5. null
6. false
7. -0

- Qualquer outro valor será **truthy**

**EVITE CONFIAR NA COERÇÃO IMPLÍCITA**

**Não faça:** 
```
const counter = 2;
if(counter)...
```

**Prefira:**
```
const counter = 2;
if(counter === 2)...
```

### NaN

definição: é um valor especial. Seu tipo é **number** e ele é **o único valor que não é igual a si mesmo**

```
NaN === NaN // false
```

#### isNaN e Number.isNaN
- isNaN() converte o valor antes de dar o resultado **EVITE**
- Number.isNaN() faz a comparação de uma maneira mair previsível **ADOTE**

# Coerção Explícita (type casting)

Definição: quando o programador expressa a intenção de converter o tipo de um dado para outro tipo, essa é conversão explícita (por exemplo, Number('12').

- Conversões explícitas
1. String()
2. Boolean()
3. Number()

# Conversão de objetos

1. Boolean = sempre serão **TRUE**
2. Number = tenta converter com **valueOf**. Se não der, fallback para **toString**. Se não der, joga um ERRO.
3. String = tenta converter com **toString**. Se não der, fallback para "valueOf". Se não der, joga um ERRO.

### Conversão de objetos no ES6

- Posso alterar o código a fundo mudando **[Symbol.toPrimitive]**, que determina o que acontecerá na conversão de um objeto para um primitivo


