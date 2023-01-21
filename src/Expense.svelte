<script>
    export let expense = [];
</script>


<article class = "single-expense">
<div class = "expense-info">
<h2>
    {expense.name}
    <button class = "amount-btn">
        <i class="fas fa-caret-down"></i>
    </button> 
</h2>
<h4>amount: ${expense.amount}</h4>
</div>
<div class = "expense-buttons">
<button class = "expense-btn edit-btn">
    <i class="fas fa-pen"></i>
</button>
<button class = "expense-btn delete-btn">
    <i class="fas fa-trash"></i>
</button>
</div>
</article>