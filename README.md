# vue-toeat

Originally from [Build with Ben: Vue 3 and TypeScript Working
Session](https://www.youtube.com/watch?v=p1eO5dZnp_Q).

Key takeaways:

- Why does `newRestaurant: Ref<Restaurant>` does not complain about non-existing
  `address`, but `const newRestaurant = ref<Restaurant>` does?
- Using TypeScript `enum` to populate `<select></select>`

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) to make the TypeScript language service aware of `.vue` types.

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
yarn
```

### Compile and Hot-Reload for Development

```sh
yarn dev
```

### Type-Check, Compile and Minify for Production

```sh
yarn build
```

### Lint with [ESLint](https://eslint.org/)

```sh
yarn lint
```
