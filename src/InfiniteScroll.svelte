<script>
  import { onMount, createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  let bottomHeight = 0;

  async function loadMore() {
    window.addEventListener("scroll", () => {
      const {
        scrollTop,
        scrollHeight,
        clientHeight,
      } = document.documentElement;
      if (clientHeight + scrollTop >= scrollHeight - bottomHeight) {
        dispatch("scroll", {});
      }
    });
  }
  onMount(() => {
    loadMore();
    return () => {
      loadMore();
    };
  });
</script>
