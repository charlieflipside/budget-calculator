<script>
import {setContext} from 'svelte';
// components
import Navbar from './Navbar.svelte';
import ExpenseList from './ExpenseList.svelte';
import expensesData from '../expenses.js';
// variables
let expenses = [...expensesData];
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
<button type = "button" class = "btn btn-primary btn-block" 
    on:click={clearExpenses}>
    clear expenses
</button>
</main>
