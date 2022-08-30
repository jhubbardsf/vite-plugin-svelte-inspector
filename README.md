

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


### Add it to the plugins array in your SvelteKit vite.config file.

```js
// filename: vite.config.js
import Inspector from '@jhubbardsf/vite-plugin-svelte-inspector';


/** @type {import('vite').UserConfig} */
const config = {
	plugins: [Inspector({ enabled: false, zIndex: 999 })],
}
```

### License

[MIT](/LICENSE)

> If you are using Svelte (haven't got it to work with sveltekit) `vite-plugin-svelte`, use the `inspector` options instead:
> https://github.com/sveltejs/vite-plugin-svelte/blob/main/docs/config.md#inspector