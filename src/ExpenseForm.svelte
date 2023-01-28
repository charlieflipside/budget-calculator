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
        <input type="text" id="name" bind:value={name}/>
        </div>
        <div class = "form-control">
            <label for="Amount">Amount</label>
            <input type="number" id="amount" bind:value={amount}/>
        </div>
        <p class = "form-empty">
    {#if name.length > 0 & amount !== null}
    Ready to Submit
    {:else}
    Please Fill Out All Form Fields
    {/if}

        </p>
        <button type = "submit" class="btn btn-block">
            Add Expense
        </button>
        <button type = "button" class = "close-btn">
            <i class="fas fa-times" />
            Close</button>
    </form>
</section>
