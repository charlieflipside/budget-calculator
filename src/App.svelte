<script>
import {setContext} from 'svelte';
// components
import Navbar from './Navbar.svelte';
import ExpenseList from './ExpenseList.svelte';
import expensesData from '../expenses.js';
import Totals from "./Totals.svelte";
import ExpenseForm from './ExpenseForm.svelte';

// variables
let expenses = [...expensesData];
// editing variables 
let setName = '';
let setAmount = '';
let setId = null;
// reactive 
$: isEditing = setId == null ? false : true;
$: total = expenses.reduce((t,n) => t + n.amount, 0);
// functions 
function removeExpense(id){
expenses = expenses.filter(item => item.id !== id);
}
function clearExpenses(){
expenses = [];
}
function addExpense({name, amount}){
let newExpense = {id: Math.random()*100, name, amount};
expenses = [newExpense, ...expenses];
}
function modifyExpense(id){
    let editExpense = expenses.find(item => item.id === id);
    setId = editExpense.id;
    setName = editExpense.name;
    setAmount = editExpense.amount;
}

//context 
setContext('remove', removeExpense);
setContext('add', addExpense);
setContext('edit', modifyExpense);

</script>

<!-- Style -->

<!-- HTML -->

<Navbar />
<main class = "content">
    <ExpenseForm name = {setName} 
        amount = {setAmount}
        id = {setId}
        isEditing = {isEditing}/> 
<ExpenseList expenses = {expenses}/>
<Totals title = "Total Amount" total = {total} />
<button type = "button" class = "btn btn-primary btn-block" 
    on:click={clearExpenses}>
    clear expenses
</button>
</main>
