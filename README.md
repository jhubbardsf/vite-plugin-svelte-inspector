

![logo](https://github.com/tanhauhau/vite-plugin-svelte-inspector/blob/master/src/logo.png?raw=true)

# vite-plugin-svelte-inspector 

Play with the [LIVE DEMO](https://stackblitz.com/edit/sveltejs-kit-template-default-gnpnjl).

## Installation

```sh
# pnpm
pnpm install @jhubbardsf/vite-plugin-svelte-inspector -D

# yarn
yarn add @jhubbardsf/vite-plugin-svelte-inspector -D

# npm
npm install @jhubbardsf/vite-plugin-svelte-inspector -D
```

## Usage
In this fork you can add an optional zIndex parameter to change the z-index on the enable bottom.

Also, meta + shift (command+shift on Mac) will enable/disable the inspector.

```js

### Add it to your SvelteKit project

```js
// filename: svelte.config.js

// for vue2
import Inspector from '@jhubbardsf/vite-plugin-svelte-inspector';

/** @type {import('@sveltejs/kit').Config} */
const config = {
  kit: {
    // ...
    vite: {
      plugins: [Inspector({ enabled: false, zIndex: 999 })],
    },
  },
};

export default config;
```

### License

[MIT](/LICENSE)

> If you are using Svelte (haven't got it to work with sveltekit) `vite-plugin-svelte`, use the `inspector` options instead:
> https://github.com/sveltejs/vite-plugin-svelte/blob/main/docs/config.md#inspector