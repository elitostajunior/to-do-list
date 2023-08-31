# Projeto back-end: "To-do List"

Este projeto idealizado no curso Web Full Stack da Labenu consiste em um back-end para um aplicativo de "to-do list" (lista de tarefas) desenvolvido com TypeScript e Express. O projeto inclui a criação, edição e recuperação de informações de usuários e tarefas. As tarefas são definidas por título, descrição, data limite, status e autor, enquanto os usuários têm nome, apelido e e-mail.

### Como usar:

1. **Configuração do Banco de Dados:**

Certifique-se de configurar corretamente as variáveis de ambiente no arquivo `.env` para se conectar ao seu banco de dados MySQL.

2. **Endpoints:**

O servidor Express está configurado para lidar com vários endpoints, que são acessados via métodos HTTP. Abaixo estão os endpoints disponíveis:

- **Criar usuário: `PUT /user`**

    - Crie um novo usuário fornecendo nome, apelido e e-mail.

- **Obter Usuário por ID: `GET /user/:id`**

    - Obtenha informações de um usuário específico fornecendo seu ID.

- **Editar Usuário: `POST /user/edit/:id`**

    - Edite informações de um usuário específico fornecendo seu ID e novos valores para nome, apelido ou e-mail.

- **Criar Tarefa: `PUT /task`**

    - Crie uma nova tarefa fornecendo título, descrição, data limite e ID do autor.

- **Obter Tarefa por ID: `GET /task/:id`**

    - Obtenha informações de uma tarefa específica fornecendo seu ID.

3. **Utilização dos Módulos:**

Cada endpoint é implementado em um módulo TypeScript correspondente na pasta `Endpoints`. Esses módulos usam funções definidas nos módulos da pasta `Data` para interagir com o banco de dados.

4. **Validações e Tratamento de Erros:**

As funções nos módulos de endpoint validam os dados de entrada e fornecem mensagens de erro apropriadas em caso de falhas.

5. **Execução do Servidor:**

O servidor pode ser iniciado executando o arquivo `index.ts`. Ele ouvirá em uma porta definida pelas variáveis de ambiente, como `PORT` (padrão: 3003).

Lembre-se de instalar todas as dependências necessárias utilizando `npm install` antes de executar o projeto.

Certifique-se de testar cada um dos endpoints usando uma ferramenta como o Postman ou Insomnia para garantir que eles estejam funcionando conforme o esperado.

### Exemplos de uso:

1. **Criar Usuário: `PUT /user`**

- Método: PUT
- URL: `http://localhost:3003/user`
- Corpo da Requisição:
~~~json
{
  "name": "João Silva",
  "nickname": "joaosilva",
  "email": "joao@example.com"
}
~~~

- Resposta de Sucesso (Status 200):
~~~json
{
  "message": "Usuário criado com sucesso!"
}
~~~

2. **Obter Usuário por ID: `GET /user/:id`**

- Método: GET
- URL: `http://localhost:3003/user/123456789`
- Resposta de Sucesso (Status 200):
~~~json
{
  "id": "123456789",
  "nickname": "joaosilva"
}
~~~

- Resposta de Erro (Status 404):
~~~json
{
  "message": "Usuário não encontrado"
}
~~~

3. **Editar Usuário: `POST /user/edit/:id`**

- Método: POST
- URL: `http://localhost:3003/user/edit/123456789`
- Corpo da Requisição:
~~~json
{
  "name": "Joana Silva"
}
~~~

- Resposta de Sucesso (Status 200):
~~~json
{
  "message": "Usuário atualizado!"
}
~~~

4. **Criar Tarefa: `PUT /task`**

- Método: PUT
- URL: `http://localhost:3003/task`
- Corpo da Requisição:
~~~json
{
  "title": "Comprar mantimentos",
  "description": "Comprar leite, pão e ovos.",
  "deadline": "15/09/2023",
  "authorId": "123456789"
}
~~~

- Resposta de Sucesso (Status 200):
~~~json
{
  "message": "Tarefa criada com sucesso!",
  "id": "1630398201007.123456789"
}
~~~

5. **Obter Tarefa por ID: `GET /task/:id`**

- Método: GET
- URL: `http://localhost:3003/task/1630398201007.123456789`
- Resposta de Sucesso (Status 200):
~~~json
{
  "id": "1630398201007.123456789",
  "title": "Comprar mantimentos",
  "description": "Comprar leite, pão e ovos.",
  "deadline": "15/09/2023",
  "status": "to do",
  "authorId": "123456789",
  "authorNickname": "joaosilva"
}
~~~

- Resposta de Erro (Status 404):
~~~json
{
  "message": "Tarefa não encontrada"
}
~~~

Esses são exemplos de como você pode usar cada endpoint do seu projeto para criar, recuperar e atualizar informações de usuários e tarefas. Lembre-se de adaptar as URLs e os dados fornecidos de acordo com o que você configurou e o que deseja testar.