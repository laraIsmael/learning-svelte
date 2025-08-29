<script lang="ts">
  import Header from "./Header.svelte";
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
  <Header name={formState.name} error={formState.error}/>
  <!-- create a paragraph element that shows the text Step: and the value of the $state step. wanting to keep $state step index 0 so we can use in a loop later on, but waring to display the steps starting in 1 = just add 1 to the display value of the step on the DOM-->
   <p>Step: {formState.step +1}</p>

  <!-- create an if statement that only shows $state error if its value is truth => pass a paragraph with a class error and show $state error -->
  {#if formState.error}
    <p class="error">{formState.error}</p>
  {/if}  

  <!-- create another if statement that checks if $state step is equal to 0
      inside the if statement:
      create a div with a label (for-name and its value is "Your name: ")and an input (type-text id-name and bind it to the $state name value)  -->
  {#if formState.step === 0}
    <div>
      <label for="name">Your name: </label>
      <input type="text" id="name" bind:value={formState.name}/>
    </div>

    <!-- create a button with a value of Next and an inline onclick callback thay checks if $state name is not empty => add 1 to step and set error to "" else => create an error message: "your name is empty. Please write your name."-->
    <button onclick={() => {
      if(formState.name !== "") {
        formState.step +=1;
        formState.error = "";
      } else {
        formState.error = "your name is empty. Please write your name.";
      }
    }}>
      Next
    </button>  
     <!-- add an if else statement that show step one and has the same next button but the input is for the $state birthday instead  -->
    {:else if formState.step === 1}
      <label for="birthday">Your Birthday: </label>
      <input type="date" bind:value={formState.birthday}/>

      <button onclick={() => { 
      if(formState.birthday !== "") {
        formState.step +=1;
        formState.error = "";
      } else {
        formState.error = "your birthday is empty. Please write your birthday.";
      }}}>Next</button>
  {/if}
</main>
