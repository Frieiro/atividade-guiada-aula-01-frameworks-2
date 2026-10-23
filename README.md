# Atividade Guiada – API CRUD para Controle de Tarefas (Spring Boot)

Disciplina: Frameworks Web II – Unilavras

API REST em Spring Boot 4.1.1 (Java 21, Maven) com CRUD de tarefas armazenadas em memória.

## Estrutura

```
src/main/java/com/example/task_api
├── controller/TaskController.java
├── modle/Task.java
├── repository/TaskRepository.java
└── TaskApiApplication.java
```

## Como executar

```bash
mvn spring-boot:run
```

Ou rode a classe `TaskApiApplication` pela IDE. A API sobe em `http://localhost:8080`.

## Endpoints

| Método | URL           | Descrição                  |
|--------|---------------|----------------------------|
| GET    | /tasks        | Lista todas as tarefas     |
| GET    | /tasks/{id}   | Busca uma tarefa pelo ID   |
| POST   | /tasks        | Cria uma nova tarefa       |
| PUT    | /tasks/{id}   | Atualiza a tarefa do ID    |
| DELETE | /tasks/{id}   | Exclui a tarefa do ID      |

### Exemplo de corpo (POST / PUT)

```json
{
  "title": "Casa",
  "description": "Organizar as tarefas de casa",
  "dueDate": "2026-12-31"
}
```

Sem `id` (ou com `"id": 0`) o ID é gerado automaticamente.

### Testando com curl

```bash
curl -X POST http://localhost:8080/tasks -H "Content-Type: application/json" \
  -d '{"title":"Casa","description":"Organizar as tarefas de casa","dueDate":"2026-12-31"}'

curl http://localhost:8080/tasks
curl http://localhost:8080/tasks/1

curl -X PUT http://localhost:8080/tasks/1 -H "Content-Type: application/json" \
  -d '{"title":"trabalho","description":"Organizar as tarefas do trabalho","dueDate":"2026-12-25"}'

curl -X DELETE http://localhost:8080/tasks/1
```
