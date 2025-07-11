# 🤖 NLW Agents

Projeto desenvolvido durante a **20ª edição da Next Level Week** da Rocketseat, focado em inteligência artificial e processamento de áudio com geração de respostas automáticas.

## 🎯 Sobre o Projeto

O NLW Agents é uma aplicação fullstack que permite criar salas de perguntas e respostas, processar áudio automaticamente e gerar respostas inteligentes utilizando a API do Google Gemini. A aplicação é perfeita para sessões de Q&A em aulas, palestras ou eventos.

## 🚀 Funcionalidades

- 📚 **Criação de salas** de perguntas e respostas
- 🎙️ **Gravação e transcrição de áudio** em tempo real
- 🤖 **Geração automática de respostas** usando IA (Google Gemini)
- 📊 **Busca por similaridade** utilizando embeddings
- 🔍 **Interface intuitiva** para visualização de perguntas e respostas

## 🛠️ Tecnologias Utilizadas

### Backend (Server)
- **Node.js** com TypeScript
- **Fastify** - Framework web rápido e minimalista
- **PostgreSQL** com pgvector para embeddings
- **Drizzle ORM** - ORM TypeScript-first
- **Google Gemini API** - IA para transcrição e geração de respostas
- **Docker** - Containerização do banco de dados
- **Zod** - Validação de schemas

### Frontend (Web)
- **React 19** com TypeScript
- **Vite** - Build tool e dev server
- **React Router Dom** - Roteamento SPA
- **TanStack Query** - Gerenciamento de estado servidor
- **React Hook Form** - Gerenciamento de formulários
- **Tailwind CSS** - Estilização utilitária
- **Radix UI** - Componentes primitivos acessíveis
- **Lucide React** - Ícones

## 🏗️ Arquitetura

```
NLW_Agents/
├── server/                 # Backend API
│   ├── src/
│   │   ├── db/            # Configuração do banco e schemas
│   │   ├── http/routes/   # Rotas da API
│   │   ├── services/      # Serviços (Gemini AI)
│   │   └── server.ts      # Servidor principal
│   ├── docker/            # Arquivos Docker
│   └── docker-compose.yml # Orquestração de containers
└── web/                   # Frontend React
    ├── src/
    │   ├── components/    # Componentes reutilizáveis
    │   ├── pages/         # Páginas da aplicação
    │   └── app.tsx        # Componente principal
    └── vite.config.ts     # Configuração do Vite
```

## ⚙️ Configuração e Execução

### Pré-requisitos

- Node.js 18+
- Docker e Docker Compose
- Chave da API do Google Gemini

### 1. Clone o repositório
```bash
git clone https://github.com/thomasbatista/NLW_Agents.git
cd NLW_Agents
```

### 2. Configuração do Backend

```bash
cd server
npm install
```

Crie o arquivo `.env` baseado no `.env.example`:
```bash
cp .env.example .env
```

Configure as variáveis de ambiente:
```env
PORT=3333
DATABASE_URL=postgresql://docker:docker@localhost:5432/agents
GEMINI_API_KEY=sua_chave_aqui
```

### 3. Configuração do Banco de Dados

Inicie o PostgreSQL com Docker:
```bash
docker-compose up -d
```

Execute as migrações:
```bash
npm run db:migrate
```

### 4. Configuração do Frontend

```bash
cd ../web
npm install
```

### 5. Execução

**Backend:**
```bash
cd server
npm run dev
```

**Frontend:**
```bash
cd web
npm run dev
```

A aplicação estará disponível em:
- Backend: `http://localhost:3333`
- Frontend: `http://localhost:5173`

## 🔗 Endpoints da API

### Rooms (Salas)
- `GET /rooms` - Listar todas as salas
- `POST /rooms` - Criar nova sala
- `GET /rooms/:roomId/questions` - Listar perguntas de uma sala

### Questions (Perguntas)
- `POST /rooms/:roomId/questions` - Criar nova pergunta

### Audio (Áudio)
- `POST /rooms/:roomId/audio` - Upload e processamento de áudio

### Health Check
- `GET /health` - Verificar status da API

## 📊 Banco de Dados

O projeto utiliza PostgreSQL com a extensão pgvector para suporte a embeddings:

- **rooms** - Armazena informações das salas
- **questions** - Armazena perguntas e respostas
- **audio_chunks** - Armazena transcrições e embeddings de áudio

## 🤝 Contribuição

Este projeto foi desenvolvido durante o evento NLW da Rocketseat. Sinta-se à vontade para fazer fork e contribuir com melhorias!

## 📝 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

---
