<script>
	let numDice = 2;
</script>

<input type="number" bind:value={numDice} min="1" max="100" />

<p>{numDice}</p>

<div style="display: flex;">
	{#each { length: numDice } as die, index}
		<div class="dice">
			{index + 1}
		</div>
	{/each}
</div>

<style>
	.dice {
		padding: 5px;
		margin: 5px;
		background: lightgray;
	}
</style>
