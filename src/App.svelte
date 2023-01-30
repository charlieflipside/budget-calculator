<script>
  import { setContext } from "svelte";
  // components
  import Navbar from "./Navbar.svelte";
  import ExpenseList from "./ExpenseList.svelte";
  import expensesData from "../expenses.js";
  import Totals from "./Totals.svelte";
  import ExpenseForm from "./ExpenseForm.svelte";

  // variables
  let expenses = [...expensesData];
  let expenseFormValues = { name: "", amount: null, id: null };
  // editing variables

  let setId = null;
  // reactive
  $: isEditing = setId == null ? false : true;
  $: total = expenses.reduce((t, n) => t + n.amount, 0);
  // functions
  function removeExpense(id) {
    expenses = expenses.filter((item) => item.id !== id);
  }
  function clearExpenses() {
    expenses = [];
  }
  function addExpense(expenseFormValues) {
    let { name, amount } = expenseFormValues;
    let newExpense = { id: Math.random() * 100, name, amount };
    expenses = [newExpense, ...expenses];
  }
  function modifyExpense(id) {
    setId = id;
    let editExpense = expenses.find((item) => item.id === id);
    expenseFormValues = editExpense;
  }

  function pushEdit( editedExpense) {
    expenses = expenses.map((item) => {
      return item.id === setId
        ? editedExpense 
        : item;
    });
    setId = null;
    console.log("changed expenses", expenses);
  }

  //context
  setContext("remove", removeExpense);
  setContext("add", addExpense);
  setContext("edit", modifyExpense);
  setContext("push", pushEdit);
</script>

<!-- Style -->

<!-- HTML -->

<Navbar />
<main class="content">
  <ExpenseForm expenseFormValues={expenseFormValues} {isEditing} />
  <ExpenseList {expenses} />
  <Totals title="Total Amount" {total} />
  <button
    type="button"
    class="btn btn-primary btn-block"
    on:click={clearExpenses}
  >
    clear expenses
  </button>
</main>
