# seashore-site

Site institucional da **SeaShore Solutions** — agência marítima (Rio de Janeiro).
Reconstrução estática do site, em substituição ao WordPress atual (Hostinger).

## Stack

- HTML/CSS/JS puro, **página única** (`index.html`), sem build e sem dependências.
- **Bilíngue PT/EN** via toggle no canto superior direito (botões `PT | EN`).
  - Strings em um dicionário JS (`I18N` no fim do `index.html`), aplicadas por `data-i18n`.
  - Idioma persiste em `localStorage` (`seashore_lang`); default segue o idioma do navegador (PT fora de EN).
- Imagens locais em `assets/img/` (baixadas do WordPress atual; ver pendência de resolução).

## Como rodar localmente

Abrir `index.html` no navegador, ou servir a pasta:

```
npx serve .        # ou: python -m http.server
```

## Deploy (alvo)

Subir o conteúdo da pasta para o `public_html` da conta Hostinger do cliente
(domínio e DNS já estão lá). Cancela-se apenas o plano WordPress.

## Pendências / a resolver antes do go-live

- **Formulário de contato:** o botão "Enviar Mensagem" usa `mailto:` provisório
  (`thiagobotelho@...`). Trocar por um serviço de formulário estático
  (Web3Forms / Formspree) e/ou pelo e-mail público real de contato.
- **Tradução EN:** rascunho feito internamente — **revisar/validar com o cliente**.
- **Página de privacidade:** o WordPress tinha `/privacidade/`. Não há link no rodapé
  por enquanto; recriar como página/âncora estática se for necessária (LGPD).
- **Imagens em baixa resolução:** as fotos são 600px de largura (originais do WP).
  Para o hero full-bleed, pedir originais em alta ao cliente ou substituir por banco.
- Conferir se há conteúdo no WP além desta home antes de desligar o plano.

## Contexto no vault

Decisões e briefing em `03_CLIENTES/SEASHORE_SOLUTIONS/PRODUTOS/SITE_INSTITUCIONAL/`
(vault Cerberus). Redesign-alvo de origem: `REFERENCIAS/seashore-responsive_novo.html`.
