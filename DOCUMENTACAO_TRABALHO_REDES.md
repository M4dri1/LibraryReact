# BIBLOTECALOCAL - SISTEMA WEB DE GERENCIAMENTO
## Documentação Técnica - Trabalho de Redes de Computadores

**Disciplina:** Redes de Computadores | **Professor:** Prof. Msc. Leonardo Assuane Duarte  
**Data:** 28/11/2025 | **Duração:** 20 minutos  
**Integrantes:** Kayky Brabo, Gabriel Araujo, Gabriel Reis, Samira Eduarda

---

## 1. VISÃO GERAL

O **BibliotecaLocal** é uma plataforma web moderna com interface roxo-temática que gerencia produtos, categorias, usuários e transações em rede local usando Docker.

### Tecnologias
- **Frontend:** React 18 + TypeScript + Vite
- **Backend:** Node.js + Express + TypeScript
- **Banco:** MySQL 8.0
- **Autenticação:** JWT
- **Imagens:** Cloudinary
- **Deploy:** Docker + Docker Compose

### Funcionalidades
✅ Autenticação com JWT (Admin/User)  
✅ CRUD de Produtos e Categorias  
✅ Sistema de Transações (Aluguel)  
✅ Avaliações com Rating (1-5 estrelas)  
✅ Upload de imagens via Cloudinary  
✅ Interface responsiva com tema roxo

---

## 2. ARQUITETURA

### Estrutura do Projeto
```
src/
├── components/     # 31 componentes React
├── server.ts       # Backend Express
├── DB/             # Conexão MySQL
├── seeders/        # Dados iniciais
└── utils/          # Utilitários
```

### Fluxo de Comunicação
```
React (Frontend) → Axios → Express API → MySQL
     ↓
   JWT Validation
     ↓
  Cloudinary (imagens)
```

### Protocolo
- **HTTP/HTTPS** com **JWT** (Bearer Token)
- **JSON** para comunicação
- **Autenticação:** Admin/User com roles

---

## 3. INSTALAÇÃO RÁPIDA

### Pré-requisitos
- Docker 20.10+
- Docker Compose 1.29+
- Git

### Passos
```bash
# 1. Clonar projeto
git clone https://github.com/seu-usuario/LibraryREACT.git
cd LibraryREACT

# 2. Configurar .env (já vem pronto)
# Verificar credenciais do Cloudinary

# 3. Iniciar
docker-compose up -d

# 4. Acessar
# App: http://localhost:8080
# BD: http://localhost:8081 (phpMyAdmin)
# Login: kayky / 123
```

### Parar
```bash
docker-compose down  # Parar e remover
docker-compose stop  # Apenas pausar
```

---

## 4. BANCO DE DADOS

### Tabelas Principais
- **users** - Usuários (admin/user)
- **products** - Produtos/Livros
- **categories** - Categorias/Autores
- **transactions** - Transações/Empréstimos
- **reviews** - Avaliações com rating

### Seeders Automáticos
✅ Usuário admin: `kayky / 123`  
✅ Tabelas criadas automaticamente  
✅ Dados iniciais no startup

---

## 5. API REST - ENDPOINTS PRINCIPAIS

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| POST | `/api/login` | Login do usuário |
| POST | `/api/register` | Registrar novo usuário |
| GET | `/api/products` | Listar produtos |
| GET | `/api/products/:id` | Detalhes do produto |
| POST | `/api/transactions` | Criar transação (aluguel) |
| GET | `/api/my-transactions` | Minhas transações |
| POST | `/api/reviews` | Criar avaliação |
| GET | `/api/reviews?product_id=1` | Avaliações do produto |

---

## 6. TESTES RÁPIDOS

```bash
# Verificar containers
docker-compose ps

# Testar login
curl -X POST http://localhost:8080/api/login \
  -H "Content-Type: application/json" \
  -d '{"username":"kayky","password":"123"}'

# Ver logs
docker-compose logs -f app
```

---

## 7. SEGURANÇA

✅ **Autenticação JWT** - Tokens com validação em cada requisição  
✅ **Autorização por Roles** - Admin/User com restrições  
✅ **Validação de Entrada** - Sanitização contra SQL Injection  
✅ **Proteção de Dados** - Senhas com hash (bcrypt)  
✅ **Variáveis de Ambiente** - Credenciais seguras

---

## 8. CONCLUSÃO

O **BibliotecaLocal** demonstra com sucesso:

✅ **Arquitetura em Camadas** - Frontend/Backend/BD separados  
✅ **Containerização Docker** - Deploy simplificado  
✅ **Segurança Robusta** - JWT + Roles + Validação  
✅ **Escalabilidade** - Arquitetura modular e pronta para crescimento  
✅ **Interface Responsiva** - Tema roxo em toda a aplicação

---

## 9. COMANDOS ÚTEIS

```bash
# Iniciar/Parar
docker-compose up -d              # Iniciar
docker-compose down               # Parar
docker-compose logs -f app        # Ver logs

# Banco de Dados
docker exec -it mysql-container2 mysql -u root -p root123
docker exec libraryreact-app-1 npm run seed

# Verificação
docker-compose ps                 # Status dos containers
docker stats                      # Uso de recursos
```

---

**Pronto para apresentação em 28/11/2025**
