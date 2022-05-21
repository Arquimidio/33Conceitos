# Coerção implícita

definição: tentativa do JavaScript de converter um **valor de tipo inesperado** para um do **tipo esperado** (a liguagem "tenta advinhar" que tipo de operação o programador pretendia realizar)

**EVITE SEMPRE QUE POSSÍVEL DEIXAR QUE ISSO ACONTEÇA**

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
