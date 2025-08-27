<script lang="ts">
import Header from './Header.svelte'

// Same name valiable and value shortcut:
// if you create a variable with the same name as the $prop you can simplify the code and have it just passed once in parenteses like the example: {name}
// the other way to do this is to set up the value on the html porsion: name={"Scott"}
// both are correact one is just shorter

// TypeScrip:
// will infer its type if you don't specify. On name TS will have the type be string since we are passing a string
// on status if we don't specify its type like we are doing here, the type would also be string since we want specifically "OPEN" | "CLOSE" we have to pass it as its shwon bellow.

let name = $state("Scott");
let status: "OPEN" | "CLOSE" = $state("OPEN");

function toggle() {
  status = status === "OPEN" ? "CLOSE" : "OPEN";
}
</script>


<Header {name} />
<input type="text" bind:value={name} />
<p>The store is {status}</p>
<button onclick={toggle}>Toggle Status</button>