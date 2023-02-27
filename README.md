# Task Manager

API da aplicação de manageamento de tasks.

## Endpoints

- Tasks
    - [Cadastrar task](#cadastrar-task)
    - Apagar task
    - [Alterar task](#alterar-task)
    - [Listar task](#listar-task)
    - [Listar todas as tasks](#listar-todas-tasks)


---

### Cadastrar Task

`POST` /tasks/api/task

| campo | tipo | obrigatório | descrição
|-------|------|:-------------:|----
| nome_task | texto | sim | titulo da task
| descricao | texto | não | um texto com detalhes sobre a task
  
  **Exemplo de corpo de requisição**

```js 
{
    nome_task: 'Criar o protótipo dos endpoints no README',
    descricao: 'Criar o protótipo dos endpoints da api de manageamento de tasks no github',
}
```

**Respostas**

| código | descrição
|-|-
|201| despesa cadastrada com sucesso
|400| a validação dos campos falhou

### Alterar task

`PATCH` /tasks/api/task

| campo | tipo | obrigatório | descrição
|-------|------|:-------------:|----
| responsavel_task | texto | sim | Nome do responsavel pela task
| prazo | data | não | um prazo para a finalização da task
| estagio_task | texto | sim | o estágio atual da task
  
  **Exemplo de corpo de requisição**

```js 
{
    responsavel_task: 'Lucas Lopes',
    prazo: '2023-02-28',
    estagio_task: 'Em andamento',
}
```

**Respostas**

| código | descrição
|-|-
|201| despesa cadastrada com sucesso
|400| a validação dos campos falhou

---

### listar task

`GET` /tasks/api/task/{id}

**Respostas**

| código | descrição
|-|-
|200| os dados da task foram retornados no corpo da resposta
|404| não existe task com o id informado

**Exemplo de corpo da resposta**
```js 
tasks{
    {   
        id: 1,
        nome_task: 'Criar o protótipo dos endpoints no README',
        created_data: '2023-02-27',
        id_responsavel: 1,
        descricao: 'Criar o protótipo dos endpoints da api de manageamento de tasks no github',
        nome_responsavel: 'Lucas Lopes',
        prazo: '2023-02-28',
        estagio_task: 'Em andamento',
    }
    {   
        id: 2
        nome_task: 'Criar o desenho do app',
        created_data: '2023-02-27',
        id_responsavel: 1,
        descricao: 'Criar o desenho das telas do app de manageamento de tasks',
        nome_responsavel: 'Lucas Lopes',
        prazo: '2023-02-28',
        estagio_task: 'Concluido',
    }
}
```
### listar todas tasks

`GET` /tasks/api/task/all

**Respostas**

| código | descrição
|-|-
|200| os dados da task foram retornados no corpo da resposta
|500| erro interno do servidor

**Exemplo de corpo da resposta**
```js 
{
    nome_task: 'Criar o protótipo dos endpoints no README',
    created_data: '2023-02-27',
    descricao: 'Criar o protótipo dos endpoints da api de manageamento de tasks no github',
    responsavel_task: 'Lucas Lopes',
    prazo: '2023-02-28',
    estagio_task: 'Em andamento',
}
```
