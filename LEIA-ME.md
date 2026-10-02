# Site Sinapse Brasil: como publicar na Vercel

## O que tem nesta pasta

| Arquivo | Para que serve |
|---|---|
| `index.html` | O site |
| `vercel.json` | Redirecionamentos 301 das páginas antigas do Wix (/quem-somos, /servicos, /clientes, /contato, blog) para as seções novas |
| `sitemap.xml` e `robots.txt` | Orientam o Google sobre o que indexar |
| `favicon.svg` | Ícone da aba do navegador |
| `img/` | Pasta para as fotos (veja o passo 1) |

## 1. Fotos

Todas as fotos já estão dentro da pasta `img/`, então o site não depende mais do Wix.
Para trocar uma foto, envie outra com o mesmo nome por cima da antiga:

| Arquivo | Onde aparece |
|---|---|
| `img/abertura-atendimento-magico-grupo-sh.jpg` | Fundo da abertura, em tela cheia |
| `img/sobre-1.jpg` e `img/sobre-2.jpg` | Quem somos (foto grande e foto menor) |
| `img/solucao-palestras.jpg` | Cartão Palestras |
| `img/solucao-treinamentos.jpg` | Cartão Treinamentos |
| `img/galeria/galeria-01.jpg` a `galeria-18.jpg` | Galeria automática |
| `img/livros/*.jpg` | Capas dos livros |
| `img/clientes/*.png` | Logos dos clientes |
| `img/chamada-final.jpg` | Fundo da chamada final |

Dica: fotos da galeria com cerca de 560 px de altura e até 150 KB deixam o site rápido.

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
