<script>
  import Child from "./Child.svelte";

  let count = $state(0)
</script>

<main>
  <div class="container">
    <h1>Learning Svelte 5</h1>
  </div>
  <div class="container">
    <button onclick={() => count++}>Count: {count}</button>
  </div>
  <div class="container">
    <Child message="Hello from Parent!"/>
  </div>
</main>

<style>
  .container {
    margin-bottom: 15px;
  }
</style>
