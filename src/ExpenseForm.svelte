<script>
    import Title from "./Title.svelte";
    let name = '';
    let amount = null;
</script>

<section class = "form">
    <Title title = "Add Expense" />
    <form class = "expense-form"> 
        <div class = "form-control">
        <label for="name">Name</label>
        <input type="text" id="name" />
        </div>
        <div class = "form-control">
            <label for="Amount">Amount</label>
            <input type="number" id="amount" />
        </div>
        <p class = "form-empty">
            Please Fill Out All Form Fields
        </p>
        <button type = "submit" class="btn btn-block">
            Add Expense
        </button>
        <button type = "button" class = "close-btn">
            <i class="fas fa-times" />
            Close</button>
    </form>
</section>
