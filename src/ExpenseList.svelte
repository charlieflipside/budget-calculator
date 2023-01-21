<script>
    import SectionTitle from './Title.svelte';
    import Expense from './Expense.svelte';
    export let expenses = [];    
</script>

<section>
    <SectionTitle title = "Expense List"/>
</section>

{#each expenses as expense, index}
<div class = "single-expense">    
    <Expense index = {index + 1} expense = {expense}/>
</div>
    {:else}
    <h2>No expenses right now</h2>
{/each}