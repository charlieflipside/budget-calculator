<script>
import { getContext } from "svelte";
    import Title from "./Title.svelte";
    export let name = '';
    export let amount = null;
    $: isEmpty = !name || !amount;
    function handleSubmit(){
    addExpense({name, amount});
        name = '';
        amount = null;
    }

// context
const addExpense = getContext('add');
</script>

<section class = "form">
    <Title title = "Add Expense" />
    <form class = "expense-form" on:submit|preventDefault={handleSubmit}> 
        <div class = "form-control">
        <label for="name">Name</label>
        <input type="text" id="name" bind:value={name}/>
        </div>
        <div class = "form-control">
        <label for="Amount">Amount</label>
        <input type="number" id="amount" bind:value={amount}/>
        </div>
        <p class = "form-empty">
    {#if !isEmpty}
    Ready to Submit
    {:else}
    Please Fill Out All Form Fields
    {/if}

        </p>
        <button type = "submit" class="btn btn-block"
        class:disabled={isEmpty}
        disabled={isEmpty}>
        Add Expense
        </button>
        <button type = "button" class = "close-btn">
        <i class="fas fa-times" />
        Close</button>
    </form>
</section>
