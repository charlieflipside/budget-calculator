<script>
import Navbar from './Navbar.svelte';
import ExpenseList from './ExpenseList.svelte';
import expensesData from '../expenses.js';

let expenses = [...expensesData];

</script>

<!-- Style -->

<!-- HTML -->

<Navbar />
<main class = "content">
<ExpenseList expenses = {expenses}/>
</main>
