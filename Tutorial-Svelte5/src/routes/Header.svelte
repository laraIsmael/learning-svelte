<script lang="ts">
  let { 
    name,
    optional_name = "Leo" 
  }: { 
    name: string,
    optional_name?: string 
  } = $props(); 

  // optional_name the ? tells TS that the value is optional so if you go to +page.svelte the implementation of <Header /> won't show an error eventhough we are not passing a value as optional_name. I'm setting a default value for it ont eh $props() object but that is also optional.
</script>


<h3>{optional_name}</h3>
<h1>Hello from {name}</h1>
<h2>{name.replaceAll('a', 'X')}</h2>