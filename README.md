# Projeto Tarefa (TODO)

## Descrição
Desenvolva um sistema de gerenciamento de tarefas (TODO) utilizando Elixir e OTP, implementando funcionalidades básicas de criação, leitura, atualização e exclusão de tarefas. Este sistema deve operar sobre uma conexão TCP, permitindo interações simples através de comandos de texto.

## Requisitos Mínimos
- **Mix Project**: Inicialize seu projeto como um projeto Mix para gerenciar suas dependências e tarefas.
- **Supervisor**: Implemente um Supervisor para garantir a resiliência e a supervisão do servidor TCP e do armazenamento de tarefas.
- **GenServer**: Use GenServer para gerenciar o estado das tarefas (adicionar, atualizar, remover e listar tarefas).
- **TCP Server**: Utilize `:gen_tcp` para criar um servidor TCP que aceitará comandos para interagir com o sistema de tarefas.
- **Distribuição**: Prepare seu aplicativo para ser potencialmente distribuído, permitindo que ele se comunique com outros nós se necessário.

## Como Usar
### Setup Inicial
1. Crie o projeto Mix:
    ```bash
    mix new tarefa --sup
    ```
2. Implemente o servidor TCP com `:gen_tcp` dentro de um GenServer.
3. Configure o Supervisor para iniciar o GenServer do TCP server.

### Implementação
1. **Servidor TCP**: Deve aceitar comandos como `ADD <tarefa>`, `REMOVE <id>`, `LIST` e `UPDATE <id> <nova tarefa>`.
2. **GenServer de Tarefas**: Mantém o estado das tarefas, implementa a lógica para adicionar, listar, remover e atualizar tarefas.
3. **Comunicação Cliente-Servidor**: Os clientes enviam comandos para o servidor via TCP, e o servidor responde com o status da solicitação ou a lista de tarefas.

### Comandos do Cliente
- Conectar ao servidor TCP usando ferramentas como `telnet` ou um cliente TCP customizado em Elixir.
- Enviar comandos seguindo o protocolo definido acima.

## Requisitos de Aceite
- Deve ser possível adicionar novas tarefas e receber um ID único para cada uma.
- Deve ser possível listar todas as tarefas atuais.
- Deve ser possível remover uma tarefa usando seu ID.
- Deve ser possível atualizar o conteúdo de uma tarefa existente usando seu ID.

## Referências
- [Documentação oficial do Elixir](https://elixir-lang.org/docs.html)
- [Guia introdutório ao Mix](https://elixir-lang.org/getting-started/mix-otp/introduction-to-mix.html)
- [Usando GenServer para estado](https://elixir-lang.org/getting-started/mix-otp/genserver.html)
- [Construindo um servidor TCP com `:gen_tcp`](https://elixir-lang.org/getting-started/mix-otp/tcp-server.html)

Dicas:
- Explore a documentação do Elixir e OTP para entender melhor os conceitos de GenServer, Supervisor e trabalhos com TCP.
- Mantenha o código bem organizado e utilize os princípios do OTP para estruturar sua aplicação.
- Teste sua aplicação com diferentes cenários e comandos para garantir que ela responde conforme esperado.
- Considere usar codificação em base62 ou base32 para gerar IDs únicos para as tarefas. Essa abordagem pode ajudar a garantir identificadores curtos e URL-amigáveis. [Veja mais sobre codificação Base62](https://en.wikipedia.org/wiki/Base62).
