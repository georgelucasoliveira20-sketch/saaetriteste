# 📋 Controle Interno — SAAETRI

Sistema web de controle interno para habilitação e credenciamento de fornecedores da SAAETRI, com suporte a:

- ✅ Checklist de fases (Habilitação, Jurídica, Fiscal/Trabalhista, Técnica, Econômica)
- 📄 Geração de PDF com parecer assinado
- 📊 Histórico de análises com filtros e exportação Excel
- 🗓️ Controle de prazos e vencimentos
- 🔍 Consulta de CNPJ via API pública (Brasil API)
- 🔗 Links diretos para certidões oficiais (Receita Federal, FGTS, TST, TCU, SICAF, etc.)
- 🔐 Autenticação de usuários via Supabase
- ☁️ Persistência de dados na nuvem (Supabase)

---

## 🚀 Como usar

### 1. Pré-requisitos

- Conta no [Supabase](https://supabase.com) (gratuito)
- Repositório no GitHub + [GitHub Pages](https://pages.github.com/) habilitado *(ou qualquer hospedagem estática)*

### 2. Configurar o Supabase

1. Crie um projeto no Supabase
2. Vá em **SQL Editor** e execute o script em [`supabase/schema.sql`](supabase/schema.sql)
3. Copie a **URL** e a **chave anon** do projeto (`Settings → API`)
4. Edite o arquivo `index.html` e substitua as variáveis:

```js
const SUPA_URL = 'https://SEU_PROJETO.supabase.co';
const SUPA_KEY = 'SUA_CHAVE_ANON_PUBLICA';
```

### 3. Publicar no GitHub Pages

1. Faça upload dos arquivos para um repositório público no GitHub
2. Vá em `Settings → Pages`
3. Defina o branch como `main` e a pasta como `/ (root)`
4. Acesse o link gerado (ex.: `https://seu-usuario.github.io/saaetri-controle-interno/`)

---

## 📁 Estrutura do projeto

```
saaetri-controle-interno/
├── index.html          # Aplicação principal (HTML + CSS + JS)
├── supabase/
│   └── schema.sql      # Script de criação das tabelas no Supabase
├── .github/
│   └── workflows/
│       └── deploy.yml  # Deploy automático via GitHub Actions (opcional)
├── .gitignore
└── README.md
```

---

## 🗄️ Banco de dados (Supabase)

O sistema usa duas tabelas principais:

| Tabela | Descrição |
|--------|-----------|
| `analises` | Registros de análise de habilitação dos fornecedores |
| `profiles` | Dados de perfil dos usuários autenticados |

As políticas de Row Level Security (RLS) garantem que cada usuário veja apenas seus próprios dados.

---

## 🔒 Segurança

- Nunca suba a **chave de serviço** (`service_role`) no código — use apenas a `anon key`
- O RLS do Supabase protege os dados por usuário
- Para ambientes de produção, configure variáveis de ambiente e um processo de build (ex.: Vite)

---

## 📦 Tecnologias

- HTML5 + CSS3 + JavaScript (Vanilla)
- [Supabase JS v2](https://supabase.com/docs/reference/javascript)
- [html2canvas](https://html2canvas.hertzen.com/) + [jsPDF](https://github.com/parallax/jsPDF) para exportação PDF
- [Brasil API](https://brasilapi.com.br/) para consulta de CNPJ
- Google Fonts — IBM Plex Sans + IBM Plex Mono

---

## 🤝 Contribuindo

Pull requests são bem-vindos. Para mudanças maiores, abra uma issue primeiro.

---

## 📜 Licença

MIT © SAAETRI — Serviço Autônomo de Água e Esgoto de Três Rios
