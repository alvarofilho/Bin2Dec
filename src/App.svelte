<script>
	let isValid = true;
	let value;
	let result;

	const validation = () => {
		isValid = !value.match(/[^01]/) ? true : false;
	}

	const convertToDec = () => {
		validation();
		if (isValid) {
			let final = parseInt(value, 2);
			result = isNaN(final) ? null : final;
		}
	};
</script>

<main>
	<h1>Bin2Dec</h1>
	<p>Enter a binary number, get a decimal conversion.</p>

	{#if !isValid}
	<p class="erro">You entered a non-binary digit (please enter only 0 or 1).</p>
	{/if}

	<input bind:value={value} type="text" minlength="1" maxlength="20" on:input={convertToDec} autoFocus>

	{#if result != null && isValid}
	<p>{result}</p>
	{:else}
	<p>🤷Waiting for a valid binary number...</p>
	{/if}

	<footer>
		<p>By <a url=#>Álvaro Filho</a></p>
		<p>Github</p>
	</footer>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	footer {
		position: fixed;
  	left: 0;
  	bottom: 0;
  	width: 100%;
  	text-align: center;
	}
</style>