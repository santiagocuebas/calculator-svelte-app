<div class='container-calculator'>
  <slot></slot>
</div>

<style>
	.container-calculator {
		display: grid;
		grid-template-columns: repeat(4, 80px);
		grid-auto-rows: min-content;
		row-gap: 5px;
		width: fit-content;
		height: fit-content;
		margin: 50px 0;
		padding: 15px;
		border-radius: 2px;
		background-color: #e6eeee;
	}
</style>
