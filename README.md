# MA Finanças Pessoais v3

Versão com:
- login individual por e-mail e senha
- banco de dados em nuvem com Supabase
- sincronização em tempo real entre você e sua esposa
- espaço compartilhado por código convite
- orçado x realizado
- categorias e subcategorias
- cartão com fechamento e vencimento
- parcelamento automático no crédito
- metas financeiras
- compromissos futuros / PIX programado

## 1) Instalar dependências

```bash
npm install
```

## 2) Criar projeto no Supabase

1. Crie um projeto no Supabase
2. Vá em **SQL Editor**
3. Execute o arquivo `supabase/schema.sql`
4. Vá em **Project Settings > API**
5. Copie:
   - `Project URL`
   - `anon public key`

## 3) Configurar variáveis

Copie `.env.example` para `.env.local` e preencha:

```env
NEXT_PUBLIC_SUPABASE_URL=https://SEU-PROJETO.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=SUA_ANON_KEY
```

## 4) Autenticação

No Supabase:
- vá em **Authentication > Providers > Email**
- habilite e-mail/senha
- em desenvolvimento, você pode deixar confirmação de e-mail desligada para facilitar testes

## 5) Rodar localmente

```bash
npm run dev
```

Abra `http://localhost:3000`

## 6) Como usar entre vocês dois

1. Você cria sua conta
2. Cria o espaço da casa
3. O app gera um **código convite**
4. Sua esposa cria a conta dela
5. Ela entra usando o código convite
6. Os dois passam a ver os mesmos dados em tempo real

## 7) Deploy na Vercel

1. Suba o projeto no GitHub
2. Importe na Vercel
3. Adicione as mesmas variáveis de ambiente
4. Faça o deploy
5. No Supabase, adicione a URL do app em:
   - **Authentication > URL Configuration > Site URL**
   - Redirect URLs se quiser expandir depois para magic link ou Google

## Observações

- esta versão usa Supabase diretamente no cliente com RLS para proteção dos dados
- o schema já inclui tabelas e políticas básicas de acesso por espaço compartilhado
- os updates de lançamentos, metas, cartões, categorias e orçamento são sincronizados em tempo real
- se quiser a próxima evolução, o ideal é criar:
  - dashboard com gráficos avançados
  - anexos/recibos
  - importação de OFX/CSV
  - fechamento mensal e fatura detalhada por cartão
