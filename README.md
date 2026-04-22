# 🎓 Autodidaktos

> Uma plataforma educacional escalável onde conteúdo gratuito encontra ferramentas poderosas de aprendizado.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![YouTube](https://img.shields.io/badge/YouTube-Calvo%20Dev-red)](https://youtube.com/@CalvoDev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Paulo%20Abreu-blue)](https://linkedin.com/in/paulo-abreu)

---

## 🎯 Sobre Autodidaktos

Autodidaktos é uma **plataforma educacional escalável** construída do zero em uma série de vídeos. O projeto demonstra:

- 🏗️ Como refatorar uma arquitetura monolítica em um design modular
- 🎬 Processo real de desenvolvimento em uma série de 15 episódios
- 🤖 Como usar IA para acelerar desenvolvimento mantendo qualidade
- 👥 Como envolver comunidade na construção de uma plataforma open source

### A Visão

Uma plataforma onde:
- **Conteúdo educacional é gratuito** - Acessível no GitHub, produzido pela comunidade
- **Ferramentas de estudo são poderosas** - Login, progresso, quizes, flashcards, anotações
- **Comunidade governa a qualidade** - Pull requests, reviews, aprovações
- **Arquitetura é escalável** - Backend modular, fácil de expandir

---

## 📺 Série de Vídeos

Este projeto é reconstruído **do zero em 15 episódios** no YouTube.

**[🎬 Assista a série completa em Calvo Dev](https://youtube.com/@CalvoDev)**

### O que você vai aprender

- ✅ Refatoração de arquitetura monolítica
- ✅ Design de API REST profissional
- ✅ Banco de dados com Prisma
- ✅ Autenticação e autorização
- ✅ Integração com GitHub e AWS
- ✅ Logging profissional
- ✅ Testes unitários e integração
- ✅ Docker e CI/CD
- ✅ Como usar IA no desenvolvimento

### Roadmap de Episódios

| Fase | Episódios | Foco |
|------|-----------|------|
| Fundação | 0-2 | Setup, arquitetura, planejamento |
| Core | 3-5 | Banco de dados, endpoints, progresso |
| Avaliações | 6-7 | Quizes e flashcards |
| Segurança | 8 | Autenticação e autorização |
| Comunidade | 9-11 | Notas, GitHub webhooks |
| Deploy | 12-13 | Docker, testes, CI/CD |
| Conclusão | 14 | Retrospectiva e próximos passos |

---

## 🤝 Como Contribuir

### 📝 Adicionar Conteúdo Educacional

Você pode contribuir com conteúdo sobre qualquer tópico educacional:

**Processo:**

1. **Faça um fork** do repositório
2. **Crie uma branch** com um nome descritivo
   ```
   git checkout -b feat/novo-curso-python
   git checkout -b add/modulo-advanced-go
   ```
3. **Organize o conteúdo** na pasta `contents/`
   ```
   contents/
   └── seu-curso/
       ├── metadata.json          (informações do curso)
       ├── 01-intro/
       │   ├── content.md        (aula em markdown)
       │   ├── quiz.json         (questões)
       │   └── flashcards.json   (memorização)
       └── 02-modulo-2/
   ```
4. **Abra um Pull Request** descrevendo:
   - O que foi adicionado
   - Por que é útil para a comunidade
   - Qualquer dependência ou prérequisito
5. **Aguarde revisão** - Será analisado e testado
6. **Pronto!** - Após aprovação, seu conteúdo estará vivo na plataforma

**Formato esperado:**

- **content.md** - Markdown com aula (pode incluir vídeos do YouTube)
- **quiz.json** - Questões de múltipla escolha ou dissertativas
- **flashcards.json** - Pares pergunta/resposta para memorização
- **metadata.json** - Nome, descrição, nível de dificuldade

**Exemplo de estrutura:**
```json
{
  "course": "Python Basics",
  "module": "01-intro",
  "title": "Introdução ao Python",
  "description": "Conceitos fundamentais da linguagem Python",
  "level": "beginner"
}
```

### 💻 Contribuir com Código

Você pode contribuir melhorando a plataforma em si:

**Áreas de interesse:**

- 🔧 **Backend** - Express, TypeScript, Prisma, APIs
- 🎨 **Frontend** - Next.js, React, UI/UX
- 🔐 **Integrações** - GitHub, AWS, webhooks
- 📊 **Features** - Analytics, gamification, certificados
- 📝 **Documentação** - Guides, docs, tutoriais

**Processo:**

1. **Abra uma issue** descrevendo a feature ou bug
2. **Aguarde feedback** - Discuta a abordagem
3. **Faça um fork** e implemente
4. **Crie um Pull Request** com:
   - Descrição clara da mudança
   - Por que essa mudança é importante
   - Testes unitários (se aplicável)
   - Documentação necessária
5. **Solicite revisão** - Code review da comunidade
6. **Merge!** - Após aprovação, sua contribuição estará no projeto

**Boas práticas:**

- ✅ Mantenha a estrutura simplista do código
- ✅ Inclua testes para novas features
- ✅ Use o logger profissional para logging
- ✅ Siga padrões já estabelecidos
- ✅ Comente código complexo
- ✅ Atualize documentação

### 🐛 Reportar Bugs

Encontrou um problema?

1. **Verifique se já foi reportado** - Procure em issues abertas
2. **Abra uma nova issue** com:
   - Título descritivo: `[BUG] Descrição breve`
   - Passos para reproduzir
   - Comportamento esperado
   - Comportamento atual
   - Ambiente (OS, Node version, etc)

### 💡 Sugerir Features

Tem uma ideia?

1. **Abra uma discussão** ou issue com: `[FEATURE] Sua ideia`
2. **Descreva a feature**:
   - O que ela faz
   - Por que seria útil
   - Como você imagina implementar
3. **Aguarde feedback** da comunidade
4. **Se aprovada**, você pode implementar ou alguém da comunidade pode!

---

## 📋 Stack Tecnológico

**Backend:**
- Node.js + Express.js
- TypeScript
- Prisma + PostgreSQL
- Winston (logging)
- Jest (testes)

**Frontend:**
- Next.js
- React + Tailwind

**Infra:**
- AWS S3 (storage de conteúdo)
- GitHub (source control e webhooks)
- Docker (containerização)

---

## 🎬 Por que esse projeto?

Este projeto serve como **referência viva** para:

1. **Arquitetura Moderna** - Como estruturar um backend escalável
2. **Desenvolvimento com IA** - Como usar IA sem perder qualidade
3. **Open Source** - Como envolver comunidade em projeto open source
4. **Series Educacionais** - Como transformar desenvolvimento em conteúdo
5. **Code Quality** - Como manter padrões em projeto comunitário

---

## 🌟 Filosofia

### Simplicidade em Primeiro Lugar
A estrutura é intencionalmente simples. Sem abstrações desnecessárias. Isso facilita:
- Novos contribuidores a entender o código
- IA a gerar novas features
- Comunidade a estender a plataforma

### Conteúdo é Comunitário
O conteúdo educacional é livre e produzido pela comunidade. Todos podem aprender, todos podem ensinar.

### Código é Referência
O código é bem documentado e estruturado. Serve como referência para boas práticas.

---

## 📚 Documentação

- 📺 **[Série de Vídeos](https://youtube.com/@CalvoDev)** - Comece aqui
- 📖 **[Documentação Técnica](./docs/)** - Detalhes de implementação
- 🗺️ **[Roadmap](./docs/TIMELINE_ROADMAP.md)** - Futuro do projeto
- 🏗️ **[Escopo](./docs/ESCOPO_FINAL_DEFINITIVO.md)** - O que será construído

---

## 📞 Comunidade

Quer fazer parte?

- 💬 **[GitHub Discussions](https://github.com/seu-usuario/autodidaktos/discussions)** - Conversas gerais
- 🐛 **[GitHub Issues](https://github.com/seu-usuario/autodidaktos/issues)** - Bugs e features
- 📺 **[YouTube - Calvo Dev](https://youtube.com/@CalvoDev)** - Série de vídeos
- 🔗 **[LinkedIn - Paulo Abreu](https://linkedin.com/in/paulo-abreu)** - Conecte-se

---

## ⭐ Se você achou útil

- Deixe uma ⭐ no GitHub
- Inscreva-se no [canal Calvo Dev](https://youtube.com/@CalvoDev)
- Compartilhe com outros desenvolvedores
- **Contribua com conteúdo ou código!**

---

## 📝 Licença

MIT © 2026 Paulo Abreu (Calvo Dev)

---

## 🙏 Agradecimentos

Obrigado por ser parte dessa jornada. Esse projeto é feito **pela comunidade, para a comunidade**.

---

**Vamo construir algo incrível juntos!** 🚀

Comece assistindo a série: [Calvo Dev no YouTube](https://youtube.com/@CalvoDev)
