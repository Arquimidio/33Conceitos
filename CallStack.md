# Call Stack (Pilha de camadas)

### Definição
Estrutura de dados que registra chamadas de fuções (basicamente, em que ponto do programa a execução se encontra).
Se uma função é chamada, ela é **adicionada (pushed) ao fim da stack** e quando ela retorna, é **retirada (popped) do fim da stack**.
Utiliza o princípio **Last in, First out** para armazenar e gerir as **chamadas das funções**.

### Resumo

1. Estrutura de dados
2. Dois métodos: **push** e **pop**
3. A primeira coisa que é mandada para a Call Stack é a main() (global)
4. Armazenamento temporário de **stack frames** (fuções + ambiente (variáveis + parâmetros))
5. Cada vez que uma função é invocada, é criado um stack frame
6. Modelo LIFO (Last in, First Out)
7. Acompanha a execução do programa
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
4. Quando a call stack está vazia, ele manda o primeiro item da queue para a call stack
5. Cada mensagem é totalmente processada antes de outra começar a ser executada

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

### Explicações
Quando o código JS é executado, são criadas duas coisas:
1.Um Global Execution Context
2.Uma Global Memory (Global Scope / Global Variable Environment)

### Resumo
1. È um ambiente no qual o código será executado
2. Basicamente, é a caixinha do Stack Frame com tudo que há nela
3. Pode ser local ou global
4. global = acessível em qualquer parte do código
5. local = acessível onde foi criado e em maiores profundidades dentro desse contexto

