# Site Sinapse Brasil: como publicar na Vercel

## O que tem nesta pasta

| Arquivo | Para que serve |
|---|---|
| `index.html` | O site |
| `vercel.json` | Redirecionamentos 301 das páginas antigas do Wix (/quem-somos, /servicos, /clientes, /contato, blog) para as seções novas |
| `sitemap.xml` e `robots.txt` | Orientam o Google sobre o que indexar |
| `favicon.svg` | Ícone da aba do navegador |
| `img/` | Pasta para as fotos (veja o passo 1) |

## 1. Fotos (recomendado, antes ou depois de publicar)

O site já funciona sem esta etapa: enquanto a pasta `img/` estiver vazia, as fotos são carregadas do Wix.
Para o site ficar independente do Wix (obrigatório se você cancelar o plano), abra cada link abaixo,
salve a imagem e coloque na pasta com exatamente o nome indicado:

| Salvar como | Link da imagem original |
|---|---|
| `img/palestra-expoprag-2025.jpg` | https://static.wixstatic.com/media/66acd7_ed91d81f99164c6cb399f5439f7516ba~mv2.jpg |
| `img/treinamento-atendimento-magico.jpg` | https://static.wixstatic.com/media/66acd7_e898ed5622e6428c8e54a44a9b4f06fd~mv2.jpg |
| `img/clientes/lucas-cunha.png` | https://static.wixstatic.com/media/e9836b_04aaadf2736945f28712e2c5bddd1573~mv2.png |
| `img/clientes/flavio-morais.png` | https://static.wixstatic.com/media/e9836b_3274fd6d9e8a42b3a869e8f9546607fd~mv2.png |
| `img/clientes/clinica-dra-limeira.png` | https://static.wixstatic.com/media/e9836b_a5e590733a3c4a099653b09a0865f387~mv2.png |
| `img/clientes/trusted-consultants.png` | https://static.wixstatic.com/media/e9836b_1e0b43616c6649e597cf168dee8c1817~mv2.png |
| `img/clientes/intermedium.png` | https://static.wixstatic.com/media/e9836b_0bd658120d614cb6bf493398f3d59ec6~mv2.png |
| `img/clientes/pinheiro-supermercado.png` | https://static.wixstatic.com/media/e9836b_796e09c76a484dbfb8a14413ef17b9db~mv2.png |
| `img/clientes/futcenter.png` | https://static.wixstatic.com/media/e9836b_d359e868ca9a4a9394589f4891199370~mv2.png |
| `img/clientes/km-engenharia.png` | https://static.wixstatic.com/media/e9836b_8bc2d21b6e014112adf316968649fd53~mv2.png |
| `img/clientes/aquaville-resort.png` | https://static.wixstatic.com/media/e9836b_40499b23fb2948ea964907fd52e27050~mv2.png |
| `img/clientes/ers-telecom.png` | https://static.wixstatic.com/media/e9836b_71becadf18d84947958b6332f2353bbd~mv2.png |
| `img/clientes/ciof.png` | https://static.wixstatic.com/media/e9836b_e1e90d1c160b4627abfc3c2aaad3e2dd~mv2.png |
| `img/clientes/artesanal-restaurante.png` | https://static.wixstatic.com/media/e9836b_a8058dcf9562432ebf1f2b02c762fdc3~mv2.png |
| `img/clientes/beckman-sementes.png` | https://static.wixstatic.com/media/e9836b_480f19e2900b4414be79878c4c46c183~mv2.png |
| `img/clientes/cliente-sinapse.png` | https://static.wixstatic.com/media/e9836b_8a7f66865e254f0ba3060309be4afd3b~mv2.png |

## 2. Publicar na Vercel

1. Crie uma conta grátis em https://vercel.com (pode entrar com o Google).
2. Clique em **Add New… > Project**.
3. O jeito mais simples sem GitHub: instale a Vercel CLI (`npm i -g vercel`), abra o terminal dentro desta pasta e rode `vercel --prod`.
   Alternativa: suba esta pasta para um repositório no GitHub e importe o repositório na Vercel (cada alteração futura publica sozinha).
4. Em **Framework Preset**, escolha **Other**. Não precisa de comando de build.
5. A Vercel gera um endereço provisório (algo como `sinapse.vercel.app`). Confira o site ali antes de mexer no domínio.

## 3. Apontar o domínio sinapseonline.com

1. No projeto da Vercel: **Settings > Domains**, adicione `www.sinapseonline.com` e `sinapseonline.com`.
   Marque o `www` como principal e o outro redirecionando para ele.
2. A Vercel mostra os registros de DNS a configurar. Em geral:
   - `A` para `sinapseonline.com` apontando para o IP que a Vercel indicar;
   - `CNAME` para `www` apontando para o endereço que a Vercel indicar.
3. Faça isso onde o domínio está registrado. Se ele foi comprado pelo Wix, edite o DNS em
   **Wix > Domínios > Gerenciar registros DNS**, ou transfira o domínio para outro registrador (Registro.br, por exemplo).
4. A propagação leva de minutos a algumas horas. A Vercel ativa o HTTPS sozinha.
5. Só cancele o plano do Wix depois que o site novo estiver no ar e as fotos estiverem na pasta `img/`.

## 4. Google, depois que estiver no ar

1. Entre no Google Search Console (https://search.google.com/search-console).
   O código de verificação antigo já está no site, então a propriedade existente deve continuar válida.
2. Em **Sitemaps**, envie `https://www.sinapseonline.com/sitemap.xml`.
3. Em **Inspeção de URL**, peça a indexação da página inicial.
4. Confira se o Perfil da Empresa no Google aponta para `https://www.sinapseonline.com`.

## Observações

- Os redirecionamentos do blog levam para a página inicial. Se quiser manter os posts, eles precisam ser migrados.
- Ao editar o texto do `index.html`, mantenha o arquivo em UTF-8 para os acentos não quebrarem.
