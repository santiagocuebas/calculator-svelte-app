<script lang="ts">
	import { evaluate } from 'mathjs';
	import Button from './components/Button.svelte';
	import BoxButton from './components/BoxButton.svelte';
	import { dataButtons } from './data/dataButtons.js';

	let input = '';

	const handleInput = (value) => {
		input += value;
	};

	const addInput = value => {
		if (value === 'Clear') return input = '';
		else if (value === '=') {
			try {
				return input = evaluate(input);
			} catch(err) {
				return input = 'Syntax Error';
			}
		}
		handleInput(value);
	};
</script>

<div class='main-container'>
	<div class='container-logo'>
		<img 
			class='logo'
			src='./freeCodeCampLogo.jpg'
			alt='Logo of freeCodeCamp'
		/>
	</div>
	<BoxButton>
		<input
			type='text'
			class='calculator-input'
			bind:value={input}
		/>
		{#each dataButtons as data (data.text)}
			<Button
				text={data.text}
				addValue={addInput}
			/>
		{/each}
	</BoxButton>
</div>

<style>
	:global(*) {
		font-size: 18px;
	}
	
	:global(body) {
		background-color: #0c0c0e;
	}
	
	.main-container {
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		justify-content: center;
		padding-top: 15px;
		font-family: Lato, sans-serif;
	}
	
	.container-logo {
		width: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
		margin: 10px
	}
	
	.logo {
		height: 50px;
	}
	
	.calculator-input {
		grid-column: 1 / span 4;
		border: none;
		border-radius: 5px;
		outline: 1px solid #838a8f;
		margin-bottom: 8px;
		padding: 6px;
		font-size: 1.3rem;
		font-weight: 600;
	}
	
	.calculator-input:focus {
		outline: 1px solid #457899;
	}
</style>
