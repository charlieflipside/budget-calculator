<script>
    import SectionTitle from './Title.svelte';
    import Expense from './Expense.svelte';
    export let expenses = [];    
</script>

<section>
    <SectionTitle title = "Expense List"/>
</section>

{#each expenses as expense}
<div class = "single-expense">    
    <Expense expense = {expense}/>
</div>
{/each}