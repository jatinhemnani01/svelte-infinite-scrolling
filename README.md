# Svelte Infinite Scroll

[![npm version](https://badge.fury.io/js/svelte-infinite-scroll.svg)](https://www.npmjs.com/package/svelte-infinite-scrolling) &bull; [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/andrelmlins/svelte-infinite-scroll/blob/master/LICENSE) &bull; [![Build Status](https://travis-ci.com/andrelmlins/svelte-infinite-scroll.svg?branch=master)](https://travis-ci.com/andrelmlins/svelte-infinite-scroll) &bull; [![Netlify Status](https://api.netlify.com/api/v1/badges/a16b6807-8f05-4e03-8ed4-33e5162155bb/deploy-status)](https://app.netlify.com/sites/svelte-infinite-scroll/deploys) &bull; [![Language grade: JavaScript](https://img.shields.io/lgtm/grade/javascript/g/andrelmlins/svelte-infinite-scroll.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/andrelmlins/svelte-infinite-scroll/context:javascript) &bull; [![Gitter](https://badges.gitter.im/svelte-infinite-scroll/community.svg)](https://gitter.im/svelte-infinite-scroll/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

Infinite Scroll Component to Svelte.

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
  <img src={item.preview[2]} alt="" />
{/each}

<InfiniteScroll on:scroll={getPosts} />
```

## Properties

Component props:

| Prop            | Type   | Default | Description                               |
| --------------- | ------ | ------- | ----------------------------------------- |
| `on:scroll`     | function | 0     | Function You Want To Run While Scrolling  |


