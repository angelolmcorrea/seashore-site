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

## Formulário de contato (Web3Forms)

A seção de contato usa um formulário (nome, e-mail, mensagem) que envia via
**Web3Forms** por AJAX, com feedback inline e honeypot anti-spam. Não precisa
de backend. **Falta 1 passo manual** para ativar:

1. Acessar https://web3forms.com e informar o **e-mail que vai receber** as
   mensagens (o e-mail de contato real da SeaShore). O serviço envia uma
   **access key** (gratuita) para esse endereço.
2. No `index.html`, trocar o valor do campo oculto
   `name="access_key"` (hoje `COLAR_ACCESS_KEY_WEB3FORMS_AQUI`) pela key recebida.
3. Testar enviando uma mensagem; ela chega no e-mail cadastrado.

Enquanto a key não for inserida, o envio retorna erro (a mensagem de erro
amigável já aparece pro usuário). O assunto e o remetente do e-mail estão nos
campos ocultos `subject` / `from_name`.

## Pendências / a resolver antes do go-live

- **Web3Forms:** inserir a access key real (passo acima) e confirmar o e-mail
  de destino com o cliente.
- **Tradução EN:** rascunho feito internamente — **revisar/validar com o cliente**.
- **Página de privacidade:** o WordPress tinha `/privacidade/`. Não há link no rodapé
  por enquanto; recriar como página/âncora estática se for necessária (LGPD).
- **Imagens em baixa resolução:** as fotos são 600px de largura (originais do WP).
  Para o hero full-bleed, pedir originais em alta ao cliente ou substituir por banco.
- Conferir se há conteúdo no WP além desta home antes de desligar o plano.

## Contexto no vault

Decisões e briefing em `03_CLIENTES/SEASHORE_SOLUTIONS/PRODUTOS/SITE_INSTITUCIONAL/`
(vault Cerberus). Redesign-alvo de origem: `REFERENCIAS/seashore-responsive_novo.html`.
