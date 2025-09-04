<script lang="ts">
	import Header from './Header.svelte';

  // import Header from "./Header.svelte";
// create a $state object to store values nd keep it reactive as it changes.
let formState = $state({
  name: "",
  birthday: "",
  step: 0,
  error: "",
})
// remember that TS will infer the type given the value passed.
 
</script>

<main>
  <Header name={formState.name} error={formState.error}>
    <p>This is the children of Header</p>
  </Header>
  
  <p>Step: {formState.step +1}</p>

  {@render formStep({ question: "What is your name?", id: "name", type: "text" })};

  {#snippet formStep({ question, id, type }: { type: string, id: string, question: string})}
    <article>
      <div>
        <label for={id}>{question}</label>
        <input {type} {id} bind:value={formState[id]}/>
      </div>
    </article>
  {/snippet}

  {#if formState.error}
    <p class="error">{formState.error}</p>
  {/if}  
</main>
