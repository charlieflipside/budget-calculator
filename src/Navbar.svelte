<script>
import { getContext } from "svelte";
const addExpense = getContext('add');

</script>

<nav class = "nav">
	<div class="nav-center">
		<h1 class = "nav-title"> Budget Calculator</h1>
		<button type = "button" class = "nav-btn" on:click={addExpense}>
			<i class="far fa-plus-square" />
			add item
		</button>
	</div>
</nav>

