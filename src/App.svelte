<script>
import {setContext} from 'svelte';
// components
import Navbar from './Navbar.svelte';
import ExpenseList from './ExpenseList.svelte';
import expensesData from '../expenses.js';
import Totals from "./Totals.svelte";
// variables
let expenses = [...expensesData];
// reactive 
$: total = expenses.reduce((t,n) => {return t + n.amount}, 0);
// functions 
function removeExpense(id){
expenses = expenses.filter(item => item.id !== id);
}
function clearExpenses(){
expenses = [];
}
//context 
setContext('remove', removeExpense);
</script>

<!-- Style -->

<!-- HTML -->

<Navbar />
<main class = "content">
<ExpenseList expenses = {expenses} />
<Totals title = "Total Amount" total = {total} />
<button type = "button" class = "btn btn-primary btn-block" 
    on:click={clearExpenses}>
    clear expenses
</button>
</main>
