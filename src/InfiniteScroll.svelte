<script>
  import { createEventDispatcher, afterUpdate } from "svelte";
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
  afterUpdate(() => {
    loadMore();
  });
</script>
