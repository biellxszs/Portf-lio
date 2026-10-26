# Nascimento Portfolio — projeto final

Pacote integrado com três experiências independentes: o portfólio principal, a demonstração imobiliária Vértice Imóveis e o site de demonstração House Burger. O build da raiz reúne as três em um único `dist/`, pronto para publicação na Vercel. Cada app React conserva seu próprio lockfile para que também possa ser instalado e publicado separadamente.

## Requisitos

- Node.js 22.12 ou superior (a versão 22 LTS é recomendada).
- npm incluído com o Node.js.
- Conexão com a internet na primeira instalação para baixar dependências.

## Rodar e publicar o conjunto completo

Na pasta `nascimento-portfolio`, execute:

```bash
npm install
npm run build
npm run preview
```

O `npm install` da raiz instala as dependências de cada app React usando os respectivos `package-lock.json`. Não é necessário instalar pacotes manualmente em cada pasta.

O preview mostra o site montado como será publicado. A saída final fica em `dist/`:

- `/` — portfólio de Gabriel Nascimento.
- `/projetos/vertice/` — Vértice Imóveis, com catálogo e interações.
- `/projetos/house-burger/` — House Burger, com cardápio e fluxo de pedido demonstrativo.

Na Vercel, importe o repositório com a raiz na pasta do projeto e mantenha o comando `npm run build` e o diretório de saída `dist`. O arquivo `vercel.json` já declara essa configuração.

## Desenvolver cada projeto separadamente

Os dois projetos React têm seus próprios `package.json` e arquivos de lock. Depois de instalar pela raiz, você pode iniciar:

```bash
npm run dev:portfolio
npm run dev:vertice
```

O House Burger é uma página HTML estática autocontida em `apps/house-burger/index.html`; pode ser aberta diretamente ou publicada como site estático. Para testar os links entre as três páginas já montadas, use `npm run build` e `npm run preview` na raiz.

Também é possível publicar o portfólio ou Vértice separadamente configurando o Root Directory da Vercel para `apps/portfolio` ou `apps/vertice-imoveis`, respectivamente. Nesse caso, publique a saída `dist` daquele app; os links internos do portfólio integrado devem ser ajustados se o portfólio for publicado sozinho, pois foram direcionados para as páginas locais deste pacote.

## O que foi ajustado nesta entrega

- Os cartões do portfólio agora mostram Vértice Imóveis e House Burger, em vez dos projetos antigos.
- O cartão do House Burger usa tipografia e arte abstrata, sem fotografia de comida no portfólio.
- Os links dos cartões abrem as demos locais dentro do mesmo site integrado.
- Os caminhos das imagens e o basename do React Router de Vértice são configurados para a subpasta `/projetos/vertice/`, sem quebrar uma publicação independente na raiz.
- O seletor de data do formulário de Vértice considera a data local do dispositivo.
- Foram removidos `node_modules` do pacote, pois são dependências geradas por máquina e sistema operacional.
- O build de integração copia as saídas compiladas para a estrutura correta sem misturar os códigos-fonte dos apps.

## Importante antes de apresentar a clientes

Os sites Vértice Imóveis e House Burger são demonstrações/conceitos, não serviços ativos. Em Vértice, imóveis, preços, regiões e características são fictícios; o formulário apenas prepara um resumo para copiar e não envia dados a um servidor. Em House Burger, os preços e itens são demonstrativos; a sacola prepara o pedido, mas não existe operação de restaurante conectada. O número de WhatsApp da hamburgueria não foi configurado. Não apresente estes dados como informações reais de empresas.

No portfólio principal, os botões de WhatsApp e Instagram usam os canais presentes na versão original enviada. Confirme que continuam corretos antes de publicar.

## Estrutura

```text
nascimento-portfolio/
├── apps/
│   ├── portfolio/          # React + Vite — página principal
│   ├── vertice-imoveis/    # React + TypeScript + Vite — site imobiliário
│   └── house-burger/       # HTML autocontido — site de demonstração
├── scripts/install.mjs     # Instala dependências dos apps com seus lockfiles
├── scripts/build.mjs       # Build e montagem das três experiências
├── package.json            # Comandos do conjunto
├── vercel.json
└── README.md
```
