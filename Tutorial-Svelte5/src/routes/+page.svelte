<script lang="ts">
import Header from './Header.svelte'

// Same name valiable and value shortcut:
// if you create a variable with the same name as the $prop you can simplify the code and have it just passed once in parenteses like the example: {name}
// the other way to do this is to set up the value on the html porsion: name={"Scott"}
// both are correact one is just shorter
let name = $state("Lara");

// TypeScrip:
// will infer its type if you don't specify. On name TS will have the type be string since we are passing a string
// on status if we don't specify its type like we are doing here, the type would also be string since we want specifically "OPEN" | "CLOSE" we have to pass it as its shwon bellow.
let status: "OPEN" | "CLOSE" = $state("OPEN");

// The rune $derived will work as a connector to a $state. meaning, when the $state associated to the $derived value change so will it.
// full_name is being displayed as a h2 bellow and it will updated when the user change the name on the input.
// a good example of use for $derived would be a cart list, imagine you have an array storing products price and a $derived could be set to the total price (the sum of all vlaues in the array) if the $state array changes an item is added or removed the $derived total value will update as well. 
let full_name = $derived(name + " " + "Ismael")

// you can name the funcion the same as the tag and just pass the short version of it as the combo of the funcion onclick here and the line commented with **** down bellow is showing
function onclick() {
  status = status === "OPEN" ? "CLOSE" : "OPEN";
}

</script>


<Header {name} />
<h2>{full_name}</h2>
<input type="text" bind:value={name} />
<p>The store is {status}</p>
<!-- **** <button {onclick}>Toggle Status</button> -->
 <!-- instead of the function on the script side and the code as above you can do what is showing bellow and have the function in line. adding js to the html portion of the code-->
 <button onclick={() => {status === "OPEN" ? "CLOSE" : "OPEN"}}>TOGGLE</button>