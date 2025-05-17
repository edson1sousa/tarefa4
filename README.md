# Projeto de Autenticação Simples

Este projeto implementa uma autenticação simples para uma aplicação de lista de tarefas utilizando Node.js e Express.

## Configuração do Projeto

1. Clone o repositório
2. Instale as dependências:
```
npm install
```
3. Inicie o servidor:
```
npm start
```
4. O servidor estará rodando em: http://localhost:3000

## Rotas Disponíveis

### Login

- **URL**: `/login`
- **Método**: `POST`
- **Corpo da Requisição**:
  ```json
  {
    "user": "admin",
    "pass": "senha123"
  }
  ```
- **Resposta de Sucesso**:
  ```json
  {
    "message": "Login bem-sucedido",
    "token": "seu-token-simples"
  }
  ```
- **Resposta de Erro**:
  ```json
  {
    "message": "Usuário ou senha incorretos"
  }
  ```

### Listar Tarefas

- **URL**: `/tasks`
- **Método**: `GET`
- **Headers**:
  - `Authorization`: seu-token-simples
- **Resposta de Sucesso**:
  ```json
  {
    "tasks": ["Tarefa 1", "Tarefa 2", "Tarefa 3"]
  }
  ```
- **Resposta de Erro**:
  ```json
  {
    "message": "Acesso proibido. Token inválido."
  }
  ```

### Adicionar Tarefa

- **URL**: `/task`
- **Método**: `POST`
- **Headers**:
  - `Authorization`: seu-token-simples
- **Corpo da Requisição**:
  ```json
  {
    "task": "Nova tarefa"
  }
  ```
- **Resposta de Sucesso**:
  ```json
  {
    "message": "Tarefa adicionada com sucesso",
    "task": "Nova tarefa"
  }
  ```
- **Resposta de Erro**:
  ```json
  {
    "message": "Acesso proibido. Token inválido."
  }
  ```

## Como Testar

### Testando a Rota de Login

1. Abra o Postman ou outro cliente HTTP
2. Crie uma nova requisição POST para `http://localhost:3000/login`
3. Na aba Body, selecione `raw` e depois `JSON`
4. Insira o seguinte JSON:
   ```json
   {
     "user": "admin",
     "pass": "senha123"
   }
   ```
5. Envie a requisição
6. Se as credenciais estiverem corretas, você receberá um token na resposta

### Testando a Rota de Tarefas

1. Abra o Postman ou outro cliente HTTP
2. Crie uma nova requisição GET para `http://localhost:3000/tasks`
3. Na aba Headers, adicione:
   - Key: `Authorization`
   - Value: `seu-token-simples`
4. Envie a requisição
5. Se o token estiver correto, você verá a lista de tarefas

## Desenvolvimento

Este projeto foi desenvolvido como parte da Tarefa 4 da Unidade 4 da disciplina de Desenvolvimento Web II.

### Branches

- `main`: Branch principal do projeto
- `autenticacao`: Branch onde a autenticação foi implementada
