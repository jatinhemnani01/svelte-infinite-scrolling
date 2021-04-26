# Svelte Infinite Scrolling

Infinite Scroll Component for Svelte.

## Installation

```bash
npm i svelte-infinite-scrolling
```

## Demo [link](https://svelte-infinite-example.netlify.app/)

## Examples

An example of how to use the library:

```js
<script>
  import { onMount } from "svelte";
  import InfiniteScroll from "./InfiniteScroll.svelte";
  let posts = [];
  async function getPosts() {
    let res = await fetch("https://meme-api.herokuapp.com/gimme/10");
    let data = await res.json();
    posts = [...posts, ...data.memes];
    console.log(posts);
  }
  onMount(() => {
    getPosts();
  });
</script>

{#each posts as item}
  <h1 style="padding:1em">{item.title}</h1>
{/each}

<InfiniteScroll on:scroll={getPosts} />
```

## Properties

Component props:

| Prop        | Type     | Default | Description                              |
| ----------- | -------- | ------- | ---------------------------------------- |
| `on:scroll` | function | 0       | Function You Want To Run While Scrolling |

### [Buy Me A Coffee](https://www.buymeacoffee.com/jatinhemnani01)
