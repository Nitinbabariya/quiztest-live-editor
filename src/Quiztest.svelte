<script lang="ts">
  import { onMount } from 'svelte';
  import quiztestHighlight from 'quiztest/public/build/extensions/quiztestHighlight.js';
  import quiztestKatex from 'quiztest/public/build/extensions/quiztestKatex.js';
  import quiztest from 'quiztest';
  import type App from './App.svelte';

  export let editorReady: boolean;
  export let code: string;

  let quiztest_node: HTMLElement;
  let app: App;

  $: {
    if (editorReady) {
      if (app) app.$destroy();
      app = quiztest
        .register(quiztestHighlight)
        .register(quiztestKatex)
        .createApp(code, quiztest_node, {});
    }
  }
</script>

<div bind:this="{quiztest_node}" class="quiztest-area"></div>

<style>
</style>
