<script lang="ts">
	export let rolledTimestamp = new Date();
	export let diceValue = 0;

	import { createEventDispatcher, onMount } from 'svelte';
	const dispatch = createEventDispatcher();

	onMount(() => {
		diceValue = randomInt(rolledTimestamp);
		dispatch('rolledValue', {
			value: diceValue
		});
	});
	
	$: {
		diceValue = randomInt(rolledTimestamp);
		dispatch('rolledValue', {
			value: diceValue
		});
	}

	function randomInt(timestamp: Date) {
		console.log(timestamp);
		let min = 1;
		let max = 6;
		return Math.floor(Math.random() * max) + min;
	}
</script>

<div class="dice">
	{diceValue}
</div>

<style>
	.dice {
		padding: 5px;
		margin: 5px;
		background: lightgray;
	}
</style>
