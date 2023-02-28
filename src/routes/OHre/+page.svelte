<script>
	let nahodneCislo = Math.floor(Math.random() * 5 + 1);
	let posledniNahodneCislo = 0;
	let body = 0;
	// identifikator timeoutu ...ta cast za rovnitkem by nemela byt potreba ale buzerovalo me to a ja nevedel proc
	let stopky = setTimeout(() => {}, 0);

	function noveNahodneCislo() {
		posledniNahodneCislo = nahodneCislo;
		nahodneCislo = Math.floor(Math.random() * 5 + 1);
		if (nahodneCislo == posledniNahodneCislo) {
			noveNahodneCislo();
		} else {
			// pokud bezi nejaky stopky(timeout) tak ho nejdriv vypneme
			if (stopky) clearTimeout(stopky);
			// za dve vteriny nastav nove nahodne cislo
			stopky = setTimeout(noveNahodneCislo, 2000);
			return nahodneCislo;
		}
	}

	function prictiBod() {
		body = body + 1;
		noveNahodneCislo();
	}

	function odectiBod() {
		body = body - 1;
	}
</script>

<br /><br /><br /><br />
<div class="tlacitka">
	{#if nahodneCislo == 1}
		<button class="cerveneTlacitko" on:click={prictiBod}>1</button>
	{:else}
		<button class="zeleneTlacitko" on:click={odectiBod}>1</button>
	{/if}

	{#if nahodneCislo == 2}
		<button class="cerveneTlacitko" on:click={prictiBod}>2</button>
	{:else}
		<button class="zeleneTlacitko" on:click={odectiBod}>2</button>
	{/if}

	{#if nahodneCislo == 3}
		<button class="cerveneTlacitko" on:click={prictiBod}>3</button>
	{:else}
		<button class="zeleneTlacitko" on:click={odectiBod}>3</button>
	{/if}

	{#if nahodneCislo == 4}
		<button class="cerveneTlacitko" on:click={prictiBod}>4</button>
	{:else}
		<button class="zeleneTlacitko" on:click={odectiBod}>4</button>
	{/if}

	{#if nahodneCislo == 5}
		<button class="cerveneTlacitko" on:click={prictiBod}>5</button>
	{:else}
		<button class="zeleneTlacitko" on:click={odectiBod}>5</button>
	{/if}
</div>
<br /><br /><br /><br /><br />
<p class="text">
	Počet bodů
	{body}
</p>

<style>
	.zeleneTlacitko {
		background-color: green;
		font-size: 30px;
		font-weight: 400;
		width: 25%;
		padding: 15px;
		margin: 5px;
	}

	.cerveneTlacitko {
		background-color: red;
		font-size: 30px;
		font-weight: 400;
		width: 25%;
		padding: 15px;
		margin: 5px;
	}

	.tlacitka {
		display: flex;
	}

	.text {
		font-weight: 500;
		font-size: 30px;
	}
</style>
