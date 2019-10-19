<script>
  import { blur, slide, scale, fade, fly } from "svelte/transition";
  import { quintOut } from "svelte/easing";
  import { getContext } from "svelte";
  export let id;
  export let name = "";
  export let amount = 0;
  let displayAmount = false;

  function toggleAmount() {
    displayAmount = !displayAmount;
  }

  const removeExpense = getContext("remove");
  const setModifiedExpense = getContext("modify");
</script>

<article class="single-expense">
  <div class="expense-info">
    <h2>
      {name}
      <button class="amount-btn" on:click={toggleAmount}>
        <i class="fas fa-caret-down" />
        toggle
      </button>
    </h2>
    {#if displayAmount}
      <!-- <h4 transition:blur>amount : ${amount}</h4> -->
      <!-- <h4 transition:scale>amount : ${amount}</h4> -->
      <!-- <h4 transition:slide>amount : ${amount}</h4> -->
      <!-- <h4 transition:fade>amount : ${amount}</h4> -->
      <h4 transition:slide>amount : ${amount}</h4>
    {/if}
  </div>
  <div class="expense-buttons">
    <button
      class="expense-btn edit-btn"
      on:click={() => setModifiedExpense(id)}>
      <i class="fas fa-pen" />
      edit
    </button>
    <button class="expense-btn delete-btn" on:click={() => removeExpense(id)}>
      <i class="fas fa-trash" />
      delete
    </button>

  </div>

</article>
