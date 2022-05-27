> If you are using `vite-plugin-svelte`, use the `inspector` options instead:
> https://github.com/sveltejs/vite-plugin-svelte/blob/main/docs/config.md#inspector

![logo](./src/logo.png)

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
      plugins: [Inspector({ enabled: true, zIndex: 999 })],
    },
  },
};

export default config;
```

### License

[MIT](/LICENSE)
