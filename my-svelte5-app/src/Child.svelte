<script lang="ts">
  let { message, count = 0 } = $props<{ message: string, count?: number }>();
</script>
<div class="p-6 bg-purple-100 border border-purple-300 rounded-lg shadow-md text-center">
  <h2 class="text-2xl font-semibold text-purple-800 mb-3">Child Component</h2>
  <!-- Display the message received from the parent -->
  <p class="text-lg text-purple-700">Message from parent: <span class="font-bold">"{message}"</span></p>
  <button onclick={() => (count++)}>increase</button>
  <button onclick={() => (count--)}>decrease</button>
  <p>value of count: {count}</p>
</div>

<style>
  /* Component-scoped CSS styles */
  .p-6 { padding: 1.5rem; }
  .bg-purple-100 { background-color: #ede9fe; }
  .border { border-width: 1px; }
  .border-purple-300 { border-color: #d8b4fe; }
  .rounded-lg { border-radius: 0.5rem; }
  .shadow-md { box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1); }
  .text-center { text-align: center; }
  .text-2xl { font-size: 1.5rem; line-height: 2rem; }
  .font-semibold { font-weight: 600; }
  .text-purple-800 { color: #5b21b6; }
  .mb-3 { margin-bottom: 0.75rem; }
  .text-lg { font-size: 1.125rem; line-height: 1.75rem; }
  .text-purple-700 { color: #6d28d9; }
  .font-bold { font-weight: 700; }
</style>
