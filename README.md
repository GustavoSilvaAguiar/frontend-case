## Project Setup

### Estrutura de pastas
```
└── pages -> Contém as páginas principais, acessadas por url.
```
```
└── layouts -> pasta que contém os arquivos para layout, contendo elementos fixos, como sidebar e header.
```
```
└── Interfaces -> contém arquivos de interface para serem utilizadas em todo o projeto se preciso.
```
```
└── Components -> pasta que contém todos os elemtos gráfico a serem utilizados nas página principais
    └── Pasta -> pasta com nome do componente pai que vai ser utilizado especificamente, para elementos de uso geral a pasta common é utilizada.
```
```
└── Assets -> contém elementos gráficos como imagens, fontes e configurações gerais de scss.
    └── Icons -> elementos com final .vue estão presentes pois são possíveis de alterar o svg mais facilmente.
```
```
└── error.vue -> página para tratar erros de rota.


# Nuxt 3 Minimal Starter

Look at the [Nuxt 3 documentation](https://nuxt.com/docs/getting-started/introduction) to learn more.

## Setup

Make sure to install the dependencies:

```bash
# npm
npm install

# pnpm
pnpm install

# yarn
yarn install

# bun
bun install
```

## Development Server

Start the development server on `http://localhost:3000`:

```bash
# npm
npm run dev

# pnpm
pnpm run dev

# yarn
yarn dev

# bun
bun run dev
```

## Production

Build the application for production:

```bash
# npm
npm run build

# pnpm
pnpm run build

# yarn
yarn build

# bun
bun run build
```

Locally preview production build:

```bash
# npm
npm run preview

# pnpm
pnpm run preview

# yarn
yarn preview

# bun
bun run preview
```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.
