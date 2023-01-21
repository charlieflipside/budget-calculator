<script>
// components
import { getContext } from "svelte";
// variables 
export let expense = [];
let amountToggle = false;
// functions 
function toggleAmount() { 
    amountToggle = !amountToggle;
}
// context
const removeExpense = getContext('remove');
</script>

<article class = "single-expense">
<div class = "expense-info">
<h2>
    {expense.name}
    <button class = "amount-btn" on:click={toggleAmount}>
        <i class="fas fa-caret-down"></i>
    </button> 
</h2>
{#if amountToggle}
    <h4>amount: ${expense.amount}</h4>
{/if}
</div>
<div class = "expense-buttons">
<button class = "expense-btn edit-btn">
    <i class="fas fa-pen"></i>
</button>
<button class = "expense-btn delete-btn" on:click={removeExpense(expense.id)}>
    <i class="fas fa-trash"></i>
</button>
</div>
</article>