# PHL Gestão — versão pronta com Supabase

Este pacote já está configurado com a Project URL e a Publishable key informadas para o projeto Supabase.

## Arquivos

- `index.html` — sistema PHL Gestão.
- `supabase-config.js` — conexão pública já configurada.
- `supabase-schema.sql` — cria a tabela segura `user_data` e as políticas RLS.

## 1. Criar a tabela do banco

1. Abra seu projeto no Supabase.
2. Vá em **SQL Editor**.
3. Clique em **New query**.
4. Abra `supabase-schema.sql`, copie todo o conteúdo e cole no editor.
5. Clique em **Run**.

## 2. Criar o usuário de acesso

1. No Supabase, vá em **Authentication > Users**.
2. Clique em **Add user**.
3. Crie um usuário usando seu e-mail e uma senha forte.
4. Use exatamente esse e-mail e senha na tela de login do PHL Gestão.

## 3. Testar localmente

Deixe `index.html` e `supabase-config.js` na mesma pasta.

Para um teste simples, abra `index.html` no Chrome ou Edge. Para recuperação de senha e para reproduzir o ambiente publicado, prefira executar o site por um servidor local, por exemplo usando a extensão Live Server do VS Code.

## 4. Publicar no GitHub Pages

Envie para o repositório pelo menos:

- `index.html`
- `supabase-config.js`

Depois vá em **Settings > Pages > Deploy from a branch**, escolha `main` e `/ (root)`.

## 5. Configurar a URL no Supabase

Quando o GitHub fornecer a URL pública, por exemplo:

`https://seuusuario.github.io/phl-gestao/`

vá no Supabase em **Authentication > URL Configuration** e configure:

- **Site URL**: a URL pública do seu GitHub Pages.
- **Redirect URLs**: adicione a mesma URL pública.

Se ainda estiver testando localmente, adicione também o endereço local que estiver usando, por exemplo `http://localhost:3000`.

## Segurança

O navegador usa apenas uma **Publishable key**. A tabela `user_data` está protegida por **Row Level Security (RLS)**, de modo que cada usuário autenticado só pode acessar sua própria linha de dados.

Nunca coloque uma chave `sb_secret_...` ou `service_role` no site.
