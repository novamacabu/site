# novamacabu.com.br · modelo 2 (corporativo)

Site institucional da Transportadora Nova Macabu. HTML estático, publicado pelo GitHub Pages.

## Estrutura

```
index.html        página única: estilos e scripts embutidos
404.html          página de erro
robots.txt        regras para buscadores
sitemap.xml       mapa do site
favicon.ico       ícone para navegadores antigos
.nojekyll         publica os arquivos como estão, sem processamento
assets/
  favicon-192.png, apple-touch-icon.png (gerados da logo)
  img/logo*.png   logo oficial (horizontal, versão branca e completa)
  fonts/          Albert Sans, autohospedada
  img/            fotos da frota em WebP e a imagem de compartilhamento (og.jpg)
```

## O que editar

- **Contatos e EmailJS:** bloco `CONFIG` no início do `<script>`, no fim do `index.html`.
  - `whatsapp`: DDI + DDD + número, só dígitos (ex.: `5522999990000`). Vazio mantém os botões apontando para a seção Atendimento.
  - `emailjs.publicKey`: chave pública do EmailJS (Account → General). Vazio mantém o formulário em modo manual (gera o número do chamado e oferece o resumo para enviar ao SAC).
- **Textos a confirmar:** marcados com `class="todo"` ou `data-todo`. Abra o site com `#revisao` no fim do endereço para destacá-los em amarelo.

## Endereço oficial

Desde 31/10/2026 o site está em **https://novamacabu.com.br** (GitHub Pages com Custom domain; o arquivo `CNAME` foi criado pelo GitHub e **não deve ser apagado**). O antigo novamacabu.github.io/site redireciona para o domínio. `www.novamacabu.com.br` também aponta para cá.

Não renomeie este repositório para `novamacabu.github.io`: isso faria `novamacabu.github.io/erp` redirecionar para o domínio e quebraria o login do ERP.

## Seções online/offline (ERP)

`dados/secoes.js` é gravado pelo ERP (Marketing › Site Oficial › Seções do site) via Make. Não edite à mão. O `<head>` do `index.html` lê o arquivo e esconde as seções offline e os links para elas. O topo (Início) fica sempre online.

## Publicar no GitHub Pages

1. Crie o repositório e envie todos os arquivos desta pasta para a branch `main`.
2. Em **Settings → Pages**, escolha *Deploy from a branch*, branch `main`, pasta `/ (root)`.
3. Em **Custom domain**, confirme `novamacabu.com.br` e, depois que o DNS propagar, marque **Enforce HTTPS**.

## DNS (no painel que gerencia a zona DNS do domínio: Hostinger ou Registro.br)

Configuração feita em 31/10/2026 (estado anterior guardado no projeto do ERP: `claude/dns-novamacabu-antes-da-troca-2026-10-31.md`):

| Tipo  | Nome | Valor                  |
|-------|------|------------------------|
| A     | @    | 185.199.108.153        |
| A     | @    | 185.199.109.153        |
| A     | @    | 185.199.110.153        |
| A     | @    | 185.199.111.153        |
| AAAA  | @    | 2606:50c0:8000::153    |
| AAAA  | @    | 2606:50c0:8001::153    |
| AAAA  | @    | 2606:50c0:8002::153    |
| AAAA  | @    | 2606:50c0:8003::153    |
| CNAME | www  | `novamacabu.github.io` |

Não altere os registros **MX**, **SPF/TXT**, **_dmarc**, **autodiscover** e **DKIM**: o e-mail @novamacabu.com.br é do Microsoft 365. O registro `erp` (CNAME para novamacabu.github.io) é do ERP.

## EmailJS

Service `service_eznl1kh` (Gmail novamacabu@gmail.com) · template interno `template_d6xeh56` · resposta automática `template_g6293un` · Reply-To `sac@novamacabu.com.br`.
Parâmetros enviados: `name`, `email`, `reply_to`, `phone`, `subject`, `message`, `ticket_id`, `time`.
Se o plano do EmailJS oferecer restrição de domínio (Account → Security), limite o uso da chave pública a `novamacabu.com.br`.
