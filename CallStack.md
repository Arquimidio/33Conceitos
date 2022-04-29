# Call Stack (Pilha de camadas)

## Definição
Estrutura de dados que registra chamadas de fuções (basicamente, em que ponto do programa a execução se encontra).
Se uma função é chamada, ela é **adicionada (pushed) ao fim da stack** e quando ela retorna, é **retirada (popped) do fim da stack**.

## Resumo

1. Estrutura de dados
2. Modelo LIFO (Last in, First Out)
3. Acompanha a execução do programa
4. Possui um limite de chamadas de função (16000 frames no Chrome)
5. Exceder o limite de chamadas vai gerar um RangeError

# Heap

## Definição
Área da memória destinada ao armazenamento de variáveis e objetos

## Resumo
1. Área da memória
2. Guarda variáveis e objetos
3. Então o heap guarda variáveis e objetos, enquanto que a call stack guarda chamadas de funções

# Queue

## Definição

No contexto do JavaScript, a **message queue (callback queue)** é uma **lista de mensagens** a serem processadas e as callbacks associadas a essas
mensagens. Ela está ligada a **eventos assíncronos** e só tem suas mensagens removidas e enviadas à call stack quando ela está vazia.

## Resumo

1. Lista de mensagens e callbacks associadas a elas
2. Mensagens são criadas sempre que ocorre um **evento**
3. Relacionada a **eventos assíncronos** (non-blocking script)
4. Envia as callbacks para a call stack apenas quando ela está vazia (não está executando outras funções)

# Event Loop

## Definição
Mecanismo responsável pela execução das callbacks presentes na **message queue**. Ele **verifica se a call stack está vazia**. Se estiver vazia,
retira o primeiro item da queue e **envia para a call stack** para ser executado.

## Resumo
1. Callbacks de código assíncrono não são executadas imediatamente
2. Essas callbacks ficam em uma fila
3. O event loop fica verificando a message queue e a call stack
4. Quando a call stack está vazia, ele manda o primeiro item da queue para a call stack
5. Cada mensagem é totalmente processada antes de outra começar a ser executada

