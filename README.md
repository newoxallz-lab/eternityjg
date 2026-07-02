# Eternity — Painel de Inteligência e Investigação Digital

## Como rodar
1. `cd eternity`
2. `npm install`
3. Copie `.env.example` para `.env` e ajuste `JWT_SECRET`, `ADMIN_USERNAME` e `ADMIN_PASSWORD`.
4. `npm start`
5. Acesse `http://localhost:3000`

Na primeira execução, um usuário administrador é criado automaticamente com as credenciais definidas em `ADMIN_USERNAME` / `ADMIN_PASSWORD` do `.env`.

## Estrutura
- `server.js` — servidor Express principal
- `routes/` — rotas de autenticação, admin e casos
- `middleware/` — autenticação JWT, controle de papéis, registro de IP
- `db/database.js` — schema SQLite (better-sqlite3) e seed do admin
- `public/` — front-end (HTML/CSS/JS puro, tema vermelho/preto)
- `uploads/` — arquivos enviados nos casos

## Funcionalidades
- Dashboard com estatísticas e gráficos
- Login/cadastro com JWT (cookie httpOnly)
- Painel admin: usuários, logs de acesso (IP), logs de atividade, configurações
- Controle de permissões por função: administrador, moderador, usuário
- Gestão de casos: criar, editar, arquivar, notas, upload de arquivos, fontes OSINT
- Registro de IP/navegador apenas com consentimento explícito (banner de privacidade)

## Segurança
- Senhas com bcrypt
- Tokens JWT com expiração de 8h
- Rotas administrativas protegidas por `authRequired` + `requireRole`
