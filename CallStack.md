# Call Stack (Pilha de camadas)

### Definição
Estrutura de dados que registra chamadas de funções (basicamente, em que ponto do programa a execução se encontra).
Se uma função é chamada, ela é **adicionada (pushed) no fim da stack** e quando ela retorna, é **retirada (popped) do fim da stack**.
Utiliza o princípio **Last in, First out** para armazenar e gerir as **chamadas das funções**.

### Resumo

1. Estrutura de dados
2. Dois métodos: **push** e **pop**
3. A primeira coisa que é mandada para a Call Stack é a main() (global)
4. Armazenamento temporário de **stack frames** (fuções + ambiente (variáveis + parâmetros))
5. Cada vez que uma função é invocada, é criado um stack frame
6. Modelo LIFO (Last in, First Out)
7. Acompanha a execução do programa (qual função está sendo executada e quais funções são chamadas de dentro dela)
8. Execução de funções feita **uma por vez**, **top to bottom**
9. É síncrona
10. Quando uma função chama outra, a chamadora fica pausada até a chamada retornar e ser retirada da stack
11. Possui um limite de chamadas de função (16000 frames no Chrome)
12. Exceder o limite de chamadas vai gerar um RangeError
13. O acúmulo excessivo de chamadas recursivas gera um Stack Overflow

# Heap

### Definição
Área da memória destinada ao armazenamento de variáveis e objetos

### Resumo
1. Área da memória
2. Guarda variáveis e objetos
3. Então o heap guarda variáveis e objetos, enquanto que a call stack guarda chamadas de funções

# Queue

### Definição

No contexto do JavaScript, a **message queue (callback queue / task queue)** é uma **lista de mensagens** 
a serem processadas e as callbacks associadas a essas mensagens. Ela está ligada a **eventos assíncronos** e 
só tem suas mensagens removidas e enviadas à call stack quando ela está vazia.

### Resumo

1. Lista de mensagens e callbacks associadas a elas
2. Mensagens são criadas sempre que ocorre um **evento**
3. Relacionada a **eventos assíncronos** (non-blocking script)
4. Envia as callbacks para a call stack apenas quando ela (a call stack) está vazia (não está executando outras funções)

# Event Loop

### Definição
Mecanismo responsável pela execução das callbacks presentes na **message queue**. Ele **verifica se a call stack está vazia**. Se estiver vazia,
retira o primeiro item da queue e **envia para a call stack** para ser executado.

### Resumo
1. Callbacks de código assíncrono não são executadas imediatamente
2. Essas callbacks ficam em uma fila
3. O event loop fica verificando a message queue e a call stack
4. Em um timeout, por exemplo, quando passa o tempo especificado, a callback é mandada para o event loop
5. Quando a call stack está vazia, ele manda o primeiro item da queue para a call stack
6. Cada mensagem é totalmente processada antes de outra começar a ser executada
7. Pode ficar starved (quando tem uma função muito lenta rodando ou muitas, isso atrasa a excução do código assíncrono, mesmo que já tenha passado o tempo determinado nele)

# JavaScript Engine

### Definição
É um **interpretador single-threaded** composto pelo memory heap e **apenas uma call stack**.

### Resumo
1. È um interpretador de código
2. É single-threaded (realiza uma ação de cada vez)
3. É composto pelo memory heap e por uma call stack

# Execution Context

### Definição
É o **ambiente no qual o código JavaScript será executado**. Pode ser um contexto global (variáveis amazenadas na **Global memory**) ou local.
Esse ambiente/ contexto determina quais variáveis estarão disponíveis para serem manipuladas.

Serve basicamente para dividir o código em partes significantes para que o Engine possa gerir toda a complexidade de interpretar e executar esse código.

O primeiro execution context a ser criado é o **Global Execution Context**

### Explicações
Quando o código JS é executado, são criadas duas coisas:
1.Um Global Execution Context (Global Object + this)
2.Uma Global Memory (Global Scope / Global Variable Environment)

### Resumo
1. É um ambiente no qual o código será executado
3. Basicamente, é a caixinha do Stack Frame com tudo que há nela
4. Sempre que um código é executado, ele é executado dentro de um execution context
5. Pode ser local ou global
6. global = acessível em qualquer parte do código
7. local = acessível onde foi criado e em maiores profundidades dentro desse contexto

### 3 tipos de Execution Context
1. Global Execution Context: É o padrão. Todo código que não está dentro de uma função está no Global Execution Context. Só existe 1 em um programa
2. Functional Execution Context: **Sempre que uma função é invocada**, um Contexto de Execução Funcional é criado
3. Eval Function Execution Context: Cada vez que eval() é usada, é criado um novo contexto de execução

### 2 fases para a criação de um execution context
1. Creation Phase
2. Execution Phase

# Creation Phase

É nessa fase que as **Function declarations** sofrem **hoisting** e é alocado espaço para as variáveis e funções.

### Passos
1. Cria um objeto global (ou objeto arguments se for a criação de um Functional Execution Context)
2. Cria o objeto **this**
3. Aloca espaço para variáveis e funções
4. Atribui undefined a vars e coloca as **function declarations na memória**

### Começa criando duas coisas
1. Lexical Environment
2. Variable Environment

### Lexical Environment
É uma estrutura que armazena os nomes de variáveis e referências a funções. É como se fosse um objeto que descreve o ambiente 

Código
```
var a = 20;
var b = 40;
function foo() {
  console.log('bar');
}
```

Lexical Environment
```
lexicalEnvironment = {
  a: 20,
  b: 40,
  foo: <ref. to foo function>
}
```

#### 3 Componentes

1. Environment Record (Declarative Environment Record (variáveis e funções + arguments object) e Object Environment Record (referências a objetos))
2. Reference to the outer environment (link ligado ao lexical environment externo para permitir a busca de variáveis nesse ambiente)
3. **this** binding (globalmente, refere-se a window, em funções, depende de como a função foi invocada)

#### Lexical Environment em pseudocódigo
```
GlobalExectionContext = {
  LexicalEnvironment: {
    EnvironmentRecord: {
      Type: "Object",
      // Identifier bindings go here
    }
    outer: <null>,
    this: <global object>
  }
}

FunctionExectionContext = {
  LexicalEnvironment: {
    EnvironmentRecord: {
      Type: "Declarative",
      // Identifier bindings go here
    }
    outer: <Global or outer function environment reference>,
    this: <depends on how function is called>
  }
}
```

### Variable Environment

Definição: é um tipo de Lexical Environment. Refere-se ao Lexical Environment que tem um Environment Record que armazena Variable Statements dentro desse execution context.

Diferença no ES6
1. Lexical Environment: guarda function declarations, let e const
2. Variable Environment: guarda var

# Execution Phase

É aqui que as variáveis são inicializadas (ligadas aos valores atribuídos) e o código é **executado linha por linha**.
Quando ela acaba, o execution context é **retirado da call stack**.

# Scope

Definição: é o atual Execution Context. Consiste em 'Onde as variáveis são acessíveis'. Cada execution context tem seu próprio **Variable Environment**. Se houver uma tentativa de acessar uma variável que não existe no contexto de execução atual, ela vai ser buscada nos contextos superiores (**Scope Chain**)!

Exceção: GERALMENTE uma variável não pode ser acessada depois que seu **execution context** foi removido da call stack (elas são locally scoped). EXCETO NO CASO DE CLOSURES (funções que retornam outra função). A função interna vai ter acesso ao Variable Environment da função externa que já saiu da call stack. Isso porque quando a função interna foi criada, seu Variable Environment englobava as variáveis presentes na função extern, **então ela pode acessar essas variáveis via Scope Chain**.

# Global variables

Definição: sempre que uma variável é criada no contexto de execução global, ela vira uma propriedade do Global Object e é acessível em qualquer parte do código. Se uma variável for criada **sem declaração** fora do strict mode, ela também fará parte do Global Object e, consequentemente, será acessível por todo o código.



