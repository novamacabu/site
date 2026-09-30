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

## Fase atual: validação (piloto)

O site está publicado só no endereço do GitHub Pages (https://novamacabu.github.io/site/). O domínio novamacabu.com.br continua apontando para o site antigo na Hostinger. Por isso o arquivo `CNAME` **não** está no repositório: se ele existir antes da troca de DNS, o GitHub redireciona para o domínio e o site novo fica inacessível.

Na virada para o domínio: crie o arquivo `CNAME` com `novamacabu.com.br`, configure o Custom domain no Pages e troque o DNS conforme abaixo. Não renomeie este repositório para `novamacabu.github.io`: isso faria `novamacabu.github.io/erp` redirecionar para o domínio e quebraria o login do ERP.

## Publicar no GitHub Pages

1. Crie o repositório e envie todos os arquivos desta pasta para a branch `main`.
2. Em **Settings → Pages**, escolha *Deploy from a branch*, branch `main`, pasta `/ (root)`.
3. Em **Custom domain**, confirme `novamacabu.com.br` e, depois que o DNS propagar, marque **Enforce HTTPS**.

## DNS (no painel que gerencia a zona DNS do domínio: Hostinger ou Registro.br)

Apague os registros A/AAAA antigos do domínio raiz que apontam para a hospedagem da Hostinger e crie:

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
| CNAME | www  | `<usuario>.github.io`  |

Não altere os registros **MX**, **SPF/TXT** e **DKIM**: são eles que mantêm os e-mails @novamacabu.com.br funcionando na Hostinger.

## EmailJS

Service `service_eznl1kh` (Gmail novamacabu@gmail.com) · template interno `template_d6xeh56` · resposta automática `template_g6293un` · Reply-To `sac@novamacabu.com.br`.
Parâmetros enviados: `name`, `email`, `reply_to`, `phone`, `subject`, `message`, `ticket_id`, `time`.
Se o plano do EmailJS oferecer restrição de domínio (Account → Security), limite o uso da chave pública a `novamacabu.com.br`.
