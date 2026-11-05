# Ritmo+ — Loja de videoaulas de música

Site responsivo pronto para personalizar, feito em **HTML, CSS e JavaScript puro** (não exige instalação de dependências).

## O que já funciona

- Página inicial profissional com layout responsivo.
- Vitrine de 8 **cursos de exemplo** e detalhes de cada curso.
- Busca, filtros por instrumento e ordenação por preço/nome.
- Carrinho com persistência no navegador (localStorage).
- Checkout que abre **link de pagamento individual** (quando cadastrado), ou **pedido pelo WhatsApp** (quando cadastrado).
- Acordeão de dúvidas, menu mobile e notificações.
- Campo `previewUrl` para exibir prévia via YouTube.

**IMPORTANTE:** este projeto é um modelo de vitrine para personalização. Cursos, preços, cargas horárias, equipe e imagens são exemplos ilustrativos. Não há cobrança ou entrega automática de vídeos enquanto você não configurar o checkout e a plataforma de alunos. Não anuncie como aulas reais sem preparar os materiais correspondentes.

## Como abrir

1. Descompacte `ritmo-mais-site.zip`.
2. Dê duplo clique em `index.html` para visualizar no navegador.
3. (Recomendado) Abra a pasta no Visual Studio Code e use a extensão Live Server para servir localmente.

## Como editar cursos, preços e conteúdos

Abra `assets/app.js`. No início há uma lista `COURSES`.

Campos principais:
- `title`: nome do curso.
- `category`: instrumento/modalidade.
- `price`, `oldPrice`: valores em reais.
- `lessons`, `duration`, `level`: informações do conteúdo.
- `topics`: tópicos que aparecem nos detalhes.
- `photo`: URL da foto.
- `previewUrl`: URL segura de incorporação do YouTube, no formato `https://www.youtube-nocookie.com/embed/ID_DO_VIDEO`.

Edite textos e nome da marca em `index.html`, cores/visual em `assets/styles.css`.

## Ativar vendas pelo Mercado Pago

1. Crie sua conta e configure um **Link de pagamento** no Mercado Pago para **cada curso**.
2. Abra `assets/app.js` e preencha `STORE_CONFIG.paymentLinks` com o ID do curso e o link real:

```js
paymentLinks: {
  'violao-essencial': 'https://mpago.la/SEU_LINK_REAL',
  'guitarra-solos': 'https://mpago.la/OUTRO_LINK_REAL',
}
```

Quando o carrinho contém **um único curso** e o link correspondente está cadastrado, o botão **Finalizar pedido** abre o checkout externo desse curso. A hospedagem gratuita do site não processa cartões nem armazena dados sensíveis.

## Ativar pedidos pelo WhatsApp

No mesmo arquivo, preencha o número comercial:

```js
whatsappNumber: '5511999999999',
```

O site abre o WhatsApp com a lista dos cursos e o total. Este é um **pedido**, não um pagamento automático.

**Carrinhos com vários cursos:** esta versão envia o pedido completo ao WhatsApp. Para criar uma cobrança única com vários cursos, é preciso um backend e uma API de pagamento, ou uma plataforma de checkout apropriada.

## Hospedar gratuitamente no GitHub Pages

1. Entre no GitHub e crie um repositório, por exemplo `ritmo-mais`.
2. Envie o **conteúdo da pasta**: `index.html`, `README.md` e a pasta `assets` (não apenas o ZIP).
3. No repositório, abra **Settings > Pages**.
4. Selecione **Deploy from a branch**, branch `main`, pasta `/ (root)` e clique em **Save**.
5. O endereço normalmente será `https://SEU-USUARIO.github.io/ritmo-mais/`.

## Sobre área do aluno, proteção de vídeos e entrega automática

HTML/JavaScript em um site estático não protege conteúdo vendido. Para vender videoaulas com acesso restrito, será necessário conectar uma solução de cursos (por exemplo, plataforma especializada) ou desenvolver:

- cadastro e login com autenticação segura;
- pagamento com confirmação via webhook;
- banco de dados para matrícula e status da compra;
- player com hospedagem e controle de acesso aos vídeos;
- recuperação de senha, políticas de privacidade e termos;
- fluxo de reembolso/suporte.

**Nunca coloque chaves secretas de pagamento no JavaScript público.**

## Imagens

Fotos ilustrativas carregam do Unsplash por URLs públicas e dependem de conexão com a internet. Substitua por imagens próprias dos cursos e instrutores antes de lançar a loja. Verifique as condições de licença de cada imagem que usar comercialmente.
