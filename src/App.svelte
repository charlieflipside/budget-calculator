<script>
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

</script>

<!-- Style -->

<!-- HTML -->

<Navbar />
<main class = "content">
<ExpenseList expenses = {expenses} removeExpense = {removeExpense}/>
</main>
