<script>
	export let text;
	export let addValue;

	const isOperator = t => {
		if (t === '+' || t === '-' || t === '*' || t === '/') return 'operator'
		else if (t === 'Clear') return 'clear'
		return ''
	};
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div 
	class={`button ${isOperator(text)}`.trimEnd()}
	on:click={() => addValue(text)}
	>
		{text}
</div>

<style>
	.button {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 75px;
		height: 50px;
		margin: 0 auto;
		border-radius: 4px;
		background-color: #3250b6;
		color: #ffffff;
		font-size: 1.1rem;
		font-weight: 700;
		cursor: pointer;
		box-shadow: 1px 1px #0c0c0c;
	}
	
	.button:active {
		background-color: #4260c6;
		color: #bbbbbb;
	}
	
	.operator {
		background-color: #2f9976;
	}
	
	.operator:active {
		background-color: #3fa986;
	}
	
	.clear {
		grid-column: 1 / span 4;
		width: 100%;
		background-color: #c72e2e;
	}
	
	.clear:active {
		background-color: #d73e3e;
	}
</style>
