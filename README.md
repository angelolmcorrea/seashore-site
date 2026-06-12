# seashore-site

Site institucional da **SeaShore Solutions** — agência marítima (Rio de Janeiro).
Reconstrução estática do site, em substituição ao WordPress atual (Hostinger).

## Stack

- HTML/CSS/JS puro, sem build e sem dependências. Páginas: `index.html` (home)
  e `privacidade.html` (política de privacidade / LGPD).
- **Bilíngue PT/EN** via toggle no canto superior direito (botões `PT | EN`).
  - Strings em um dicionário JS (`I18N` no fim do `index.html`), aplicadas por `data-i18n`/`data-i18n-ph`.
  - Idioma persiste em `localStorage` (`seashore_lang`), **compartilhado entre as páginas**; default segue o idioma do navegador (PT fora de EN).
- Seções da home: hero, stats, empresa, serviços, galeria, áreas, **parceiros e clientes**, certificações, contato.
- Imagens locais em `assets/img/` (baixadas do WP atual). Logos de parceiros em `assets/img/partners/`. Logo própria 3S em `assets/img/seashore-3s.png` (favicon temporário).
- **SEO:** meta description, Open Graph/Twitter, canonical e JSON-LD (Organization).
- **Acessibilidade:** skip link, foco visível, `aria-*` no menu mobile, form e botões de idioma.

## Como rodar localmente

Abrir `index.html` no navegador, ou servir a pasta:

```
npx serve .        # ou: python -m http.server
```

## Deploy (alvo)

Subir o conteúdo da pasta para o `public_html` da conta Hostinger do cliente
(domínio e DNS já estão lá). Cancela-se apenas o plano WordPress.

## Formulário de contato (Web3Forms)

A seção de contato usa um formulário (nome, e-mail, mensagem) que envia via
**Web3Forms** por AJAX, com feedback inline e honeypot anti-spam. Não precisa
de backend. **ATIVO desde 2026-06-11**: access key vinculada a
`operations@seashoresolutions.com.br` no campo oculto `access_key` do
`index.html`. O assunto e o remetente do e-mail estão nos campos ocultos
`subject` / `from_name`. (Se o destinatário mudar um dia, gerar key nova em
https://web3forms.com com o e-mail novo e trocar o valor do campo.)

## Pendências / a resolver antes do go-live

- **Política de privacidade é MINUTA** (`privacidade.html`) — **requer revisão jurídica /
  do cliente** antes do go-live.
- **Favicon definitivo:** hoje usa a logo 3S como temporário; trocar pela logo que o
  cliente vai enviar.
- **Tradução EN:** rascunho interno (home + privacidade) — **revisar/validar com o cliente**.
- **Imagens em baixa resolução:** as fotos da home são 600px (originais do WP).
  Para o hero full-bleed, pedir originais em alta ou substituir por banco.
- ~~**Montserrat:** confirmar com o cliente se entra~~ — **cliente pediu incluir (2026-06-10)**; logo em `assets/img/partners/montserrat.png`, na grade de parceiros.
- Conferir se há conteúdo no WP além da home antes de desligar o plano.

## Contexto no vault

Decisões e briefing em `03_CLIENTES/SEASHORE_SOLUTIONS/PRODUTOS/SITE_INSTITUCIONAL/`
(vault Cerberus). Redesign-alvo de origem: `REFERENCIAS/seashore-responsive_novo.html`.
