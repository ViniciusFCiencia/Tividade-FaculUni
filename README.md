# Tividade-FaculUni

## Parte 1: Identificação de Violações de SOLID e Clean Code

A seguir, estão listadas as principais violações encontradas no código original do sistema de biblioteca.

---

### 1. Violação do SRP (Single Responsibility Principle)

- **Classe**: `GerenciadorBiblioteca`
- **Métodos**: `AdicionarUsuario`, `RealizarEmprestimo`, `RealizarDevolucao`
- **Descrição**: A classe `GerenciadorBiblioteca` concentra diversas responsabilidades, como cadastro de livros, usuários, controle de empréstimos e envio de notificações.
- **Por que é uma má prática**: Viola o princípio da responsabilidade única, dificultando a manutenção e reutilização do código. Uma mudança em uma funcionalidade pode afetar outras que não estão relacionadas.

---

### 2. Violação do OCP (Open/Closed Principle)

- **Classe**: `GerenciadorBiblioteca`
- **Método**: `RealizarEmprestimo`, `RealizarDevolucao`
- **Descrição**: A lógica de envio de notificações está diretamente implementada na classe, impedindo a extensão de novas formas de notificação sem modificar o código original.
- **Por que é uma má prática**: Isso viola o princípio de que o código deve estar aberto para extensão, mas fechado para modificação. Para incluir novas formas de notificação (como WhatsApp ou push), seria necessário alterar a classe diretamente.

---

### 3. Violação do DIP (Dependency Inversion Principle)

- **Classe**: `GerenciadorBiblioteca`
- **Métodos**: `EnviarEmail`, `EnviarSMS`
- **Descrição**: A classe depende diretamente de implementações concretas de envio de mensagens.
- **Por que é uma má prática**: Isso dificulta a substituição e o teste dos componentes. O ideal seria depender de abstrações, como uma interface `INotificador`.

---

### 4. Violação de Clean Code: Métodos com muitas responsabilidades

- **Método**: `RealizarEmprestimo`
- **Descrição**: O método realiza várias ações: encontra o livro e o usuário, verifica disponibilidade, atualiza o estado do livro, adiciona o empréstimo, envia e-mails e SMS.
- **Por que é uma má prática**: Um método deve fazer apenas uma coisa. Isso torna o código mais legível, testável e reutilizável.

---

### 5. Violação de Clean Code: Nomes pouco significativos

- **Métodos**: `AdicionarLivro`, `AdicionarUsuario`
- **Descrição**: Os nomes são genéricos e não indicam claramente a responsabilidade do método em contexto mais amplo.
- **Por que é uma má prática**: Nomes significativos facilitam a leitura e manutenção do código por outros desenvolvedores.

---

Nome: VINICIUS FERREIRA CIENCIA       RA: 3022103392


## Parte 2: Refatoração

A refatoração proposta foi baseada na separação das responsabilidades em serviços específicos, aplicação de interfaces para inversão de dependência e melhoria da legibilidade do código. O código refatorado pode ser encontrado no arquivo `BibliotecaRefatorada.cs`.


