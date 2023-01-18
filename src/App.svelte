<script>
import Navbar from './Navbar.svelte';
import Title from './Title.svelte';
let fruits = ['apple', 'orange','banana'];

function fruitLength(fruit){
return(
	fruit + '-' + fruit.length
)
} 

</script>

<!-- Style -->

<!-- HTML -->

<Navbar />
<Title />
<Title title = "Add Item"/>

{#each fruits as fruit}
	<Title title = {fruitLength(fruit)}/>
{/each}

