# 🎓 Autodidaktos - Plataforma Educacional Escalável

> Reconstruindo uma plataforma de estudos do zero. Backend modular, conteúdo comunitário, ferramentas de aprendizado integradas.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-green)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-14%2B-blue)](https://www.postgresql.org/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED)](https://www.docker.com/)

## 📖 Sobre Este Projeto

Autodidaktos é uma **plataforma educacional escalável** onde:

- 🎯 **Conteúdo educacional gratuito** (markdown, vídeos, quizes, flashcards)
- 💳 **Plataforma paga** (login, progresso, ferramentas de estudo, anotações)
- 👥 **Comunidade contribui** conteúdo via GitHub PRs
- 🏗️ **Backend modular** separado do frontend
- ☁️ **Infraestrutura escalável** (S3, PostgreSQL, Docker)
- 📝 **Anotações sincronizadas** com GitHub do usuário

### Por que reescrever?

A versão anterior era um **monolito Next.js** com:
- ❌ Frontend e backend acoplados
- ❌ Difícil escalar features independentes
- ❌ Comunidade não conseguia contribuir facilmente
- ❌ Sem integração com serviços externos
- ❌ SQLite em produção (péssimo)

Agora temos uma **arquitetura moderna e escalável**.

---

## 🎬 Série de Vídeos

Este projeto é reconstruído do zero em uma **série de 15 episódios** no YouTube.

- 📺 **Canal:** [Calvo Dev - YouTube](https://youtube.com/@CalvoDev)
- 🔄 **Frequência:** 1-2 episódios por semana
- ⏱️ **Duração:** ~45 min por episódio
- 📍 **Status:** Em produção (Episódio X de 15)
- 🔔 **Inscreva-se** para receber notificações de novos episódios!

### Episódios Planejados

| Ep | Título | Status |
|----|--------|--------|
| 0 | Motivação | Planejado |
| 1 | Arquitetura | Planejado |
| 2 | Setup Node + Express | Planejado |
| 3 | Banco de Dados (Prisma) | Planejado |
| 4-5 | Rastreamento de Progresso | Planejado |
| 6-7 | Quizes e Flashcards | Planejado |
| 8 | Autenticação (JWT + GitHub) | Planejado |
| 9-11 | Comunidade (Notas, Webhooks) | Planejado |
| 12-13 | Deploy (Docker, CI/CD) | Planejado |
| 14 | Conclusão e Retrospectiva | Planejado |

**[Ver roadmap completo](./docs/TIMELINE_ROADMAP.md)**

---

## 🏗️ Arquitetura

### Estrutura do Backend (Express + TypeScript)

```
backend/
├── src/
│   ├── app/
│   │   ├── controllers/        # Controladores Express (recebem requisições)
│   │   ├── routes/             # Rotas Express (mapeiam URLs)
│   │   ├── entities/           # Entidades/DTOs (estrutura de dados)
│   │   ├── usecases/           # Lógica de negócio (orquestração)
│   │   └── middleware/         # Middlewares (autenticação, validação, logging)
│   │
│   ├── infra/
│   │   ├── logging/            # Sistema de logging (Winston)
│   │   │   ├── logger.ts       # Logger principal (singleton)
│   │   │   ├── formats.ts      # Formatos customizados
│   │   │   ├── levels.ts       # Níveis de log
│   │   │   └── transports.ts   # Configuração de outputs
│   │   │
│   │   ├── prisma/             # Banco de dados (Prisma ORM)
│   │   │   └── client.ts       # Cliente Prisma
│   │   │
│   │   ├── aws/                # Integração AWS S3
│   │   │   └── s3-client.ts    # Cliente S3
│   │   │
│   │   └── github/             # Integração GitHub API
│   │       └── github-client.ts # Cliente GitHub
│   │
│   ├── app.ts                  # Configuração Express
│   ├── server.ts               # Entry point (inicia servidor)
│   └── __tests__/              # Testes (Jest + Supertest)
│
├── logs/                       # Logs rotacionados (gitignored)
├── dist/                       # Build compilado (gitignored)
├── prisma/
│   ├── schema.prisma           # Schema do banco
│   └── migrations/             # Histórico de migrações
├── Dockerfile                  # Container do backend
├── docker-compose.yml          # Orquestração local
├── jest.config.js              # Configuração Jest
├── tsconfig.json               # Configuração TypeScript
├── .env.example                # Variáveis de exemplo
└── package.json                # Dependências e scripts

```

### Monorepo Completo

```
Autodidaktos (Monorepo)
├── backend/                    # Node.js + Express + TypeScript + Jest
│   └── (estrutura acima)
│
├── frontend/                   # Next.js refatorado
│   ├── app/                    # App router
│   └── components/             # UI reutilizáveis
│
├── contents/                   # Conteúdo educacional (GitHub source)
│   └── certifications/
│       └── aws-clf-c02/        # MVP: AWS CLF-C02
│           ├── metadata.json
│           ├── 01-intro/
│           │   ├── content.md
│           │   ├── quiz.json
│           │   └── flashcards.json
│           ├── 02-compute/
│           └── ...
│
├── docs/                       # Documentação da série
│   ├── TIMELINE_ROADMAP.md
│   ├── ESCOPO_FINAL_DEFINITIVO.md
│   └── ...
│
├── docker-compose.yml          # Desenvolvimento local (principal)
├── .github/
│   └── workflows/
│       ├── sync-content.yml    # PR → S3 sync
│       └── ci-backend.yml      # CI/CD do backend
│
├── README.md                   # Este arquivo
└── LICENSE
```

### Filosofia: Simplicidade para IA

A estrutura é **intencionalmente simplista** para facilitar desenvolvimento com IA:

✅ **Nomes claros** - Controllers, Usecases, Entities
✅ **Sem abstrações desnecessárias** - Sem injeção de dependência complexa
✅ **Escalável** - Fácil adicionar novos controllers/usecases
✅ **Testável** - Estrutura clara facilita testes
✅ **IA-Friendly** - Código simples para gerar com prompts diretos

Veja episódios da série sobre como usar IA no desenvolvimento! 📺

### Stack Tecnológico

**Backend:**
- Node.js 18+ + Express.js
- TypeScript (type-safe)
- Prisma ORM + PostgreSQL
- Winston (logging profissional)
- Jest + Supertest (testes)
- JWT + OAuth2 (GitHub)
- AWS SDK v3 (S3)
- Octokit (GitHub API)

**Frontend:**
- Next.js (refatorado)
- React + Tailwind
- (em desenvolvimento)

**Infra & DevOps:**
- PostgreSQL 14+
- AWS S3 + CloudFront CDN
- Docker + Docker Compose
- GitHub Actions (CI/CD)
- Winston Daily Rotate (log rotation)

---

## 🚀 Começando

### Pré-requisitos

- Node.js 18+
- Docker & Docker Compose
- Git
- (Opcional) AWS account + S3 bucket

### Setup Local (Desenvolvimento)

```bash
# 1. Clone o repositório
git clone https://github.com/seu-usuario/autodidaktos.git
cd autodidaktos

# 2. Copie o arquivo de environment
cp .env.example .env

# 3. Inicie os containers (PostgreSQL + Backend)
docker-compose up -d

# 4. Execute migrations
cd backend
npm install
npx prisma migrate dev

# 5. Inicie o servidor em desenvolvimento
npm run dev
```

O servidor estará disponível em `http://localhost:3000`.

### Verificar Setup

```bash
# Health check do backend
curl http://localhost:3000/api/health

# Acessar Prisma Studio (visualizar banco)
npx prisma studio
```

---

## 📁 Estrutura do Conteúdo

O conteúdo fica em `/contents/` e é o **source of truth**:

```
contents/certifications/aws-clf-c02/
├── metadata.json              # Metadados do curso
├── 01-intro/
│   ├── content.md            # Aula (markdown + embeds)
│   ├── quiz.json             # Questões
│   └── flashcards.json       # Memorização
├── 02-compute/
│   └── ...
└── 12-final-review/
    └── ...
```

**Fluxo:**
1. Community abre PR com conteúdo novo
2. GitHub Actions valida estrutura
3. Você revisa e aprova
4. PR merge → webhook dispara
5. Conteúdo sincroniza pra S3
6. Frontend serve do CloudFront

---

## 🤝 Contribuindo

### Adicionar Novo Conteúdo

```bash
# 1. Fork do repositório
# 2. Crie uma branch
git checkout -b feat/novo-modulo

# 3. Adicione conteúdo em contents/
contents/certifications/aws-clf-c02/
└── novo-modulo/
    ├── content.md
    ├── quiz.json
    └── flashcards.json

# 4. Commit e push
git commit -m "Add: novo módulo"
git push origin feat/novo-modulo

# 5. Abra um Pull Request
# Descrição deve incluir:
# - O que foi adicionado
# - Por que é útil
# - Se há dependências
```

### Encontrou um Bug?

```bash
# Abra uma issue
# Título: [BUG] Descrição breve
# Descrição: passos para reproduzir + resultado esperado
```

### Tem Uma Ideia?

```bash
# Abra uma discussão
# Título: [IDEIA] Sua sugestão
# Converse com a comunidade antes de começar
```

---

## 🤖 Desenvolvendo com Claude Code

Este projeto foi construído **com IA** e é otimizado para desenvolvimento **assistido por IA**.

### Por que essa estrutura?

A estrutura **intencionalmente simplista** facilita:
- ✅ Gerar novos controllers com prompts simples
- ✅ Adicionar usecases mantendo consistência
- ✅ Criar entidades/DTOs rapidamente
- ✅ Escrever testes sem boilerplate
- ✅ Integrar com Prisma/AWS/GitHub sem complexidade

**Veja na série de vídeos como usar IA no desenvolvimento!** 📺

### Prompts Disponíveis

Todos os prompts estão em `/docs/`:

- `PROMPT-CLAUDE-CODE.md` - Gerar projeto completo do zero
- `PROMPT-LOGGER.md` - Adicionar logger profissional

### Exemplo: Criar Nova Feature

```
Crie um controller UserController para:
- GET /api/users/:id → Retornar usuário por ID
- POST /api/users → Criar novo usuário
- PATCH /api/users/:id → Atualizar usuário

Estrutura esperada:
- Arquivo: src/app/controllers/user.controller.ts
- Métodos: getById(), create(), update()
- Usar logger para registrar operações
- Validar entrada com try/catch
- Retornar resposta padronizada

Gere o código completo!
```

Passos:
1. Abra Claude Code
2. Cole o prompt acima
3. Gere o código
4. Copie pra `src/app/controllers/user.controller.ts`
5. Crie a rota em `src/app/routes/`
6. Pronto!

### Boas Práticas com IA

✅ **Ser específico** - Descrever exatamente o que quer
✅ **Referenciar estrutura** - Mencionar pastas esperadas
✅ **Usar padrões existentes** - Mencionar Controllers/Usecases já criados
✅ **Pedir validação** - "Valide entrada", "Trate erros"
✅ **Incluir logging** - "Use logger.info/error"
✅ **Testes** - "Gere testes com Jest"

---

## 📋 Variáveis de Ambiente

```env
# Backend
NODE_ENV=development
PORT=3000
LOG_LEVEL=debug

# Database
DATABASE_URL=postgresql://user:password@localhost:5432/autodidaktos_dev

# JWT
JWT_SECRET=seu-secret-aqui-mude-em-producao
JWT_REFRESH_SECRET=seu-refresh-secret
JWT_EXPIRY=15m
JWT_REFRESH_EXPIRY=7d

# GitHub OAuth
GITHUB_CLIENT_ID=seu-app-id
GITHUB_CLIENT_SECRET=seu-app-secret
GITHUB_CALLBACK_URL=http://localhost:3000/api/auth/github/callback

# AWS (para S3 - não obrigatório no MVP)
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=sua-key
AWS_SECRET_ACCESS_KEY=seu-secret
S3_BUCKET_NAME=autodidaktos-content

# Frontend
NEXT_PUBLIC_API_URL=http://localhost:3000
```

---

## 📝 Sistema de Logging Profissional

O projeto usa **Winston** com configuração profissional:

### Níveis de Log

```
fatal  → Erros críticos que derrubam a app
error  → Erros que precisam atenção
warn   → Alertas (dados inválidos, falhas esperadas)
info   → Eventos importantes (servidor iniciado, user criado)
http   → Requisições HTTP
debug  → Informações de debug
trace  → Detalhes muito específicos
```

### Saída de Logs

**Development (Console colorido):**
```
2024-04-22 10:30:15 INFO    🚀 Server running on port 3000
2024-04-22 10:30:16 HTTP    GET /api/health { status: 200, duration: '2ms' }
2024-04-22 10:30:17 DEBUG   HealthCheck requested { userAgent: 'Mozilla/5.0' }
2024-04-22 10:30:18 ERROR   Database connection failed
```

**Production (JSON estruturado em arquivos):**
```json
{"timestamp":"2024-04-22 10:30:15","level":"info","message":"Server running"}
{"timestamp":"2024-04-22 10:30:16","level":"http","method":"GET","path":"/api/health","status":200}
```

### Arquivos de Log (Rotacionados)

```
logs/
├── error-2024-04-22.log      # Apenas erros (14 dias de retenção)
├── app-2024-04-22.log        # Todos os logs (7 dias)
└── http-2024-04-22.log       # HTTP requests (3 dias)
```

### Usar Logger no Código

```typescript
import { logger } from '../infra/logging/logger';

// Em controladores
export class UserController {
  async create(req: Request, res: Response) {
    logger.info('Creating user', { email: req.body.email });
    
    try {
      const user = await createUserUsecase.execute(req.body);
      logger.info('User created', { userId: user.id });
      res.json(user);
    } catch (error) {
      logger.error('Failed to create user', error, { email: req.body.email });
      res.status(400).json({ error: error.message });
    }
  }
}

// Em usecases
export class CreateUserUsecase {
  async execute(data) {
    logger.debug('Validating user data', { email: data.email });
    
    if (!data.email) {
      logger.warn('User creation with invalid email', { data });
      throw new Error('Invalid email');
    }

    const user = await prisma.user.create({ data });
    logger.info('User persisted to database', { userId: user.id });
    return user;
  }
}

// Para requisições HTTP
logger.http('POST /api/users', {
  status: 201,
  duration: '45ms',
  userId: user.id
});
```

### Configuração

Arquivo `.env`:
```env
NODE_ENV=development
LOG_LEVEL=debug
```

Logs automáticos:
- ✅ Middleware HTTP loga todas as requisições
- ✅ Erros não tratados são capturados
- ✅ Stack traces de exceptions
- ✅ Não loga health checks (reduz ruído)

---

```bash
cd backend

# Rodar testes
npm test

# Com coverage
npm run test:coverage

# Em modo watch
npm run test:watch
```

---

## 🐳 Docker

```bash
# Iniciar tudo
docker-compose up

# Com logs
docker-compose up -d && docker-compose logs -f

# Parar
docker-compose down

# Resetar (cuidado!)
docker-compose down -v
```

---

## 📊 Banco de Dados

### Migrations

```bash
cd backend

# Criar nova migration
npx prisma migrate dev --name seu-nome

# Aplicar migrations em produção
npx prisma migrate deploy

# Reset local (cuidado!)
npx prisma migrate reset
```

### Visualizar Dados

```bash
# Prisma Studio (interface web)
npx prisma studio

# Abre em http://localhost:5555
```

---

## 🔄 GitHub Actions (CI/CD)

### Sync de Conteúdo

Quando uma PR é **merged** em `main`:

1. GitHub Actions detecta
2. Valida estrutura de conteúdo
3. Faz upload pra S3
4. Dispara webhook ao backend
5. Backend atualiza banco

Arquivo: `.github/workflows/sync-content.yml`

---

## 📚 Documentação

Toda a documentação de planejamento está em `/docs/`:

- `TIMELINE_ROADMAP.md` - Episódios detalhados
- `ESCOPO_FINAL_DEFINITIVO.md` - Escopo completo
- `01-arquitetura-backend.md` - Tech stack
- `TEMPLATE-ROTEIRO.md` - Como gravas episódios

---

## 🎯 MVP (Fase 1)

**O que está incluído:**
- ✅ Autenticação (JWT + GitHub OAuth)
- ✅ Listagem de cursos/módulos
- ✅ Visualização de conteúdo
- ✅ Rastreamento de progresso
- ✅ Quizes e avaliações
- ✅ Flashcards com SRS
- ✅ Anotações por módulo
- ✅ Sincronização com GitHub
- ✅ Docker + CI/CD

**Roadmap (Fase 2+):**
- 🔄 Pagamento (Stripe)
- 🔄 Certificados digitais
- 🔄 Analytics avançado
- 🔄 Mais cursos
- 🔄 Sistema de reputação

---

## 🌍 Deploy

### Vercel (Frontend)

```bash
# Automático quando merge em main
# ou configure em Vercel dashboard
```

### Seu Servidor (Backend)

```bash
# Build
npm run build

# Start
npm start

# Com PM2
pm2 start dist/index.js --name autodidaktos
```

### AWS (Recomendado)

- ECS/Fargate para backend
- CloudFront para S3
- RDS para PostgreSQL
- ElastiCache para Redis (roadmap)

---

## 📞 Comunidade & Redes Sociais

- 💬 **Discussions:** GitHub Discussions
- 🐛 **Bugs:** Issues com label `bug`
- 💡 **Ideias:** Issues com label `enhancement`
- 📧 **LinkedIn:** [Paulo Abreu | LinkedIn](https://linkedin.com/in/paulo-abreu)
- 📺 **YouTube:** [Calvo Dev](https://youtube.com/@CalvoDev)

---

## 📝 Licença

MIT © 2026 Paulo Abreu (Calvo Dev) - Veja [LICENSE](./LICENSE)

---

## 🙏 Obrigado

Se você achou útil, considere:
- ⭐ Star neste repositório
- 🔗 Compartilhar com outros
- 🤝 Contribuir com PR
- 💬 Dar feedback

---

## 🎬 Veja Também

- [Série de Vídeos](https://youtube.com/@CalvoDev)
- [LinkedIn - Paulo Abreu](https://linkedin.com/in/paulo-abreu)
- [Documentação Técnica](./docs/)
- [Roadmap](./docs/TIMELINE_ROADMAP.md)
- [Escopo Completo](./docs/ESCOPO_FINAL_DEFINITIVO.md)

---

**Pronto para começar?**

```bash
git clone https://github.com/seu-usuario/autodidaktos.git
cd autodidaktos
docker-compose up -d
npm run dev
```

Acesse `http://localhost:3000/api/health` 🚀
