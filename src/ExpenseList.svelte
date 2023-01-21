<script>
    import SectionTitle from './Title.svelte';
    import Expense from './Expense.svelte';
    export let expenses = [];    
    export let removeExpense;
</script>

<section>
    <SectionTitle title = "Expense List"/>
</section>

{#each expenses as expense}  
    <Expense expense = {expense} removeExpense = {removeExpense}/>
    {:else}
    <h2>No expenses right now</h2>
{/each}