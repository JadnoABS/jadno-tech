# jadno-tech

Website pessoal com a finalidade de expor minhas experiências profissionais e acadêmicas, projetos e meios de contato.
Feito com [Vue.js](https://vuejs.org/), [Marked.js](https://github.com/markedjs/marked) e [Vue3 Carousel](https://github.com/ismail9k/vue3-carousel)

![Tela do website jadno.tech](public/jadno-tech.png)

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Run End-to-End Tests with [Cypress](https://www.cypress.io/)

```sh
npm run test:e2e:dev
```

This runs the end-to-end tests against the Vite development server.
It is much faster than the production build.

But it's still recommended to test the production build with `test:e2e` before deploying (e.g. in CI environments):

```sh
npm run build
npm run test:e2e
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
