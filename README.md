# Checkpoint 2 - DevOps (Api Java e SQL na VM)

# 🐱‍🏍 **Projeto DimDim API**

## 📌 Descrição
Este projeto consiste em uma aplicação Java Spring Boot integrada a um banco de dados MySQL, utilizando Docker para containerização e execução em ambiente cloud (Azure VM).

A aplicação implementa um CRUD de transações financeiras.

## 🧱 Arquitetura
* 🐳 **Docker**
* ☕ **Java 17 + Spring Boot**
* 🗄️ **MySQL 8**
* ☁️ **Azure Virtual Machine**

A comunicação entre os containers ocorre por meio de uma rede Docker interna.

## 📦 Containers

| Serviço | Nome | Porta |
| :--- | :--- | :--- |
| MySQL | mysql-dimdim | 3306 |
| API | api-dimdim | 8080 |

---

## 🛠️ Como Operar o Projeto

### 1. Ligar a VM
Conectar via SSH normalmente:
```bash
ssh admlinux@IP_DA_VM
```
### 2. Subir containers
```bash
docker start mysql-dimdim
```
*Aguarde cerca de 10 segundos para o banco inicializar.*
```bash
docker start api-dimdim
```

### 3. Verificar se os containers estão funcionando
Mostrar que tudo está rodando corretamente:
```bash
docker ps
```

---

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
