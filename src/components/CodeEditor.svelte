<script>
    import { onMount } from 'svelte';
    import Prism from 'prismjs';
    import 'prismjs/themes/prism-tomorrow.css'; // Use any theme you like
    
    let code = `function sayHello() {
      print("Hello, world!");
    }`;
    let language = 'Python';
  
    onMount(() => {
      Prism.highlightAll();
    });
  
    $: Prism.highlightAll();
  </script>
  
  <style>
    .editor {
      font-family: monospace;
      background: #2d2d2d;
      color: white;
      padding: 20px;
      margin-bottom: 20px;
      white-space: pre-wrap;
    }
  </style>
  
  <textarea bind:value={code} class="editor"></textarea>
  <pre class="editor"><code class="language-{language}">{code}</code></pre>
  