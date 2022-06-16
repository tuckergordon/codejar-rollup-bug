<script lang="ts">
  import { CodeJar } from "codejar";
  import { onMount } from "svelte";

  const highlight = (editor: HTMLElement) => {
    const code = editor.textContent;
    // Do something with code and set html.
    editor.innerHTML = code;
  };

  onMount(() => {
    const jar = CodeJar(document.querySelector(".editor"), highlight);
  });
</script>

<div class="editor" />

<style>
  .editor {
    height: 400px;
    width: 400px;
    background: lightblue;
  }
</style>
