<script>
    export let expense = [];
    export let index; 
</script>

<div>
    <h1>
    {index} - {expense.name}
    </h1>
    <h2>{expense.id}</h2>
    <p>{expense.amount}</p>
</div>