<script>
  import { onMount } from 'svelte';
  export let enabled = true;
  export let zIndex = 'auto';
  let open;
  let x;
  let y;

  $: ({ file, line, column } = parse(open));

  onMount(() => {
    console.log("SvelteInspector Mounted");
    document.body.addEventListener('mouseover', mouseover);
    document.body.addEventListener('mousemove', mousemove);
    document.body.addEventListener('click', click);

    const handleKeyboard = ({ repeat, metaKey, shiftKey }) => {
      if ((metaKey && shiftKey)) {
        enabled = !enabled;
      }
    }

    document.addEventListener('keydown', handleKeyboard)

    return () => {
      document.body.removeEventListener('mouseover', mouseover);
      document.body.removeEventListener('mousemove', mousemove);
      document.body.removeEventListener('click', click);
      document.addEventListener('keydown', handleKeyboard)
    };
  });

  function mousemove(event) {
    if (!enabled) return;
    x = event.x;
    y = event.y;
  }
  function mouseover(event) {
    if (!enabled) return;
    open = event.target.__svelte_meta;
  }
  function click() {
    if (!enabled || !file) return;
    fetch(`/__open-in-editor?file=${file}:${line}:${column}`);
  }
  function parse(open) {
    if (open) {
      const { loc: { file, line, column } } = open;
      return { file, line: line + 1, column: column + 1 };
    }
    return {};
  }
</script>

<div class="toggle" class:enabled on:click={() => (enabled = !enabled)} style="--z-index: {zIndex};">
  <img
    src="https://github.com/tanhauhau/vite-plugin-svelte-inspector/blob/master/src/logo.png?raw=true"
    alt="logo"
  />
</div>

{#if enabled && file}
  <ul class="overlay" style:left="{x + 10}px" style:top="{y + 10}px" style="--z-index: {zIndex};">
    <li>file: {'<'}{file}{'>'}</li>
    <li>line: {line}</li>
    <li>column: {column}</li>
  </ul>
{/if}

<style>
  .overlay {
    position: fixed;
    border: 2px dashed #666;
    background-color: rgba(0, 0, 0, 0.8);
    color: #fff;
    padding: 10px;
    border-radius: 5px;
    text-align: left;
    z-index: var(--z-index);
  }
  ul {
    list-style-type: none;
  }
  .toggle {
    border-radius: 50%;
    position: fixed;
    bottom: 20px;
    right: 20px;
    height: 50px;
    width: 50px;
    background: white;
    border: 2px solid red;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    z-index: var(--z-index);
  }
  img {
    width: 80%;
    height: 80%;
    margin-top: 3px;
  }
  .toggle:not(.enabled) {
    border-color: gray;
    border-style: dashed;
    filter: grayscale(1);
  }
  .toggle:hover {
    background: #facece;
  }
</style>
