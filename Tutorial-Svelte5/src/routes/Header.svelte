<script lang="ts">
  // importing snippet as the type of children, passing children as prop will give you access to the children passed inside the component on the file where its exported to the DOM
  // on the HTML down below you use @render and pass children as a function.
	import type { Snippet } from "svelte";

  let { 
    children,
    name,
    error,
    optional_name = "Leo" 
  }: { 
    children: Snippet,
    name: string,
    error: string,
    optional_name?: string 
  } = $props(); 

  // optional_name the ? tells TS that the value is optional so if you go to +page.svelte the implementation of <Header /> won't show an error eventhough we are not passing a value as optional_name. I'm setting a default value for it ont eh $props() object but that is also optional.
</script>

<div>
  <h3>{optional_name}</h3>
  <h1>{name}'s Form'</h1>
</div>
<h2 class="test">{name.replaceAll('a', 'X')}</h2>
{@render children()}
<h2 class="error">{error}</h2>

<style>
  /* this style is unique to this file  if you have another file with a div or a class test this won't be passed. You can still create global css variables by adding a :global before the style block as shown below.*/
  div {
    background: green;
  }

  :global(.error) {
    color: red;
  }

  .test {
    background: blue;
  }
</style>