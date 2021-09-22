<script lang="ts">
    import Dice from './_Dice.svelte';

	let numDice = 2;
    let totalDice = 0;

    let rolledTimestamp: Date;
</script>

<input type="number" bind:value={numDice} min="1" max="100" />

<button on:click={() => {
        totalDice = 0;
        rolledTimestamp = new Date()}
    } 
    style="border:black">
    Roll All
</button>



<div style="display: flex;">
	{#each { length: numDice } as die, index}
		<Dice on:rolledValue={(event) => (totalDice += event.detail.value)}  {rolledTimestamp}></Dice>
	{/each}
</div>

<p>{totalDice}</p>

