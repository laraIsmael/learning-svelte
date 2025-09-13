<script lang="ts">

// create a $state object to store values nd keep it reactive as it changes.
// remember that TS will infer the type given the value passed.

let formState = $state({
  answer: {},
  name: "",
  birthday: "",
  color: "",
  step: 0,
  error: "",
})

const QUESTIONS = [
  {
    question: 'What is your name?',
    id: 'name',
    type: 'text',  
  },
  {
    question: 'What is your birthday?',
    id: 'birthday',
    type: 'date',  
  },
  {
    question: 'What is your favorite color?',
    id: 'color',
    type: 'color',  
  }
];

function nextStep(id: string) {
  if(formState.answer[id]) {
    formState.step += 1;
    formState.error = ''
  } else {
    formState.error = 'Please fill up the form.';
  }
}

$effect(() => {
  //will run once the component is mounted and never again. 
  console.log('on mounted')
  return () => {
    // will run when component is unmounted or destroyed
    // before the effect re-runs
    console.log('on unmounted')
  }
})
</script>

<main>

  {#if formState.step >= QUESTIONS.length}
		<p>Thank you!</p>
	{:else}
		<p>Step: {formState.step + 1}</p>
	{/if}

  {#each QUESTIONS as { id, question, type }, index (id)}
    {#if formState.step === index}
      {@render formStep({ question, id, type })}
    {/if}  
  {/each}

  <!-- {JSON.stringify(formState)} -->

  {#if formState.error}
    <p class="error">{formState.error}</p>
  {/if}  
</main>

  {#snippet formStep({ question, id, type }: { type: string, id: string, question: string})}
    <article>
      <div>
        <label for={id}>{question}</label>
        <input {type} {id} bind:value={formState.answer[id]}/>
      </div>
      <button onclick={() => nextStep(id)}>Next</button>
    </article>
  {/snippet}


<style>
    :global(.error) {
    color: red;
  }
</style>