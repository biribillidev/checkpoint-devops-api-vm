# Checkpoint 2 - DevOps (Api Java e SQL na VM)

## 📌 Descrição
Este projeto consiste em uma aplicação Java Spring Boot integrada a um banco de dados MySQL, utilizando Docker para containerização e execução em ambiente cloud (Azure VM).

A aplicação implementa um CRUD de transações financeiras.

---

1. Ligar a VM
Conectar via SSH normalmente:

ssh adminlnx@IP_DA_VM

2. Verificar containers
docker ps -a

Deve aparecer:

mysql-dimdim api-dimdim

3. Subir containers (se não estiverem rodando)
docker start mysql-dimdim

espera ~10 segundos

docker start api-dimdim
## 🧪 Testes da API

### Listar transações
```bash
curl -X GET http://localhost:8080/api/transacoes
```

### Criar transação
```bash
curl -X POST http://localhost:8080/api/transacoes \
 -H "Content-Type: application/json" \
 -d '{"descricao":"Compra mercado","valor":100}'
```

### Atualizar transação
```bash
curl -X PUT http://localhost:8080/api/transacoes/1 \
 -H "Content-Type: application/json" \
 -d '{"descricao":"Alterado","valor":200,"dataTransacao":"2024-06-18T00:00:00"}'
```

### Remover transação
```bash
curl -X DELETE http://localhost:8080/api/transacoes/{id}
```

---

## 🌐 Acesso à aplicação

* **Local (dentro da VM):** `curl http://localhost:8080/api/transacoes`
* **Externo (via navegador):** http://20.48.228.123:8080/api/transacoes
