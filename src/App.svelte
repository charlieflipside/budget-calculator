<script>
import {setContext} from 'svelte';
// components
import Navbar from './Navbar.svelte';
import ExpenseList from './ExpenseList.svelte';
import expensesData from '../expenses.js';
// variables
let initialExpenses = [...expensesData];
let addedExpenses = [];
$: expenses = [...initialExpenses, ...addedExpenses];

// functions 
function removeExpense(id){
expenses = expenses.filter(item => item.id !== id);
}
function clearExpenses(){
expenses = [];
}
function addExpense(){
addedExpenses = [...addedExpenses, {id: 1, name: "hi", amount: 5}];
}

//context 
setContext('remove', removeExpense);
setContext('add', addExpense);
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
