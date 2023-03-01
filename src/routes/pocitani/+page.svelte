<script>
	// zakladani promennych
	let vysledek = 0;
	let hodnota1 = 0;
	let hodnota2 = 0;
	let nahodneCislo = Math.floor(Math.random() * 10);
	let cinitel1 = Math.floor(Math.random() * 10 + 1);
	let cinitel2 = Math.floor(Math.random() * 10 + 1);
	let vysledek2 = 0;
	let body = 0;
	let zobrazeniKontroly = 0;
	let stopky = setTimeout(() => {}, 0);

	// funkce
	function soucet() {
		vysledek = hodnota1 + hodnota2;
		return vysledek;
	}

	function rozdil() {
		vysledek = hodnota1 - hodnota2;
		return vysledek;
	}

	function nasobeni() {
		vysledek = hodnota1 * hodnota2;
		return vysledek;
	}

	function deleni() {
		vysledek = hodnota1 / hodnota2;
		return vysledek;
	}

	
	function kontrola() {
		if (cinitel1 * cinitel2 == vysledek2) {
			body = body + 1;
			zobrazeniKontroly = 1
			if (stopky) clearTimeout(stopky);
			stopky = setTimeout(resetPrikladu, 2000);
			
		} else {
			body = body;
			zobrazeniKontroly = 1
			if (stopky) clearTimeout(stopky);
			stopky = setTimeout(resetPrikladu, 2000)
			
		}
		return body;
	}

	function resetPrikladu () {
		zobrazeniKontroly = 0
		cinitel1 = Math.floor(Math.random() * 10 + 1);
		cinitel2 = Math.floor(Math.random() * 10 + 1);
	}
</script>

<h1 class="nadpis1">Počítání</h1>

<!-- policko na zadani cisla -->
<input bind:value={hodnota1} type="number" />
<input bind:value={hodnota2} type="number" />

<!-- on:click={funkce} zavola funkci -->
<div class="boxTlacitek">
	<button class="tlacitko" on:click={soucet}>+</button>
	<button class="tlacitko" on:click={rozdil}>-</button>
	<button class="tlacitko" on:click={nasobeni}>*</button>
	<button class="tlacitko" on:click={deleni}>/</button>
</div>

{vysledek}

<br />
<br />
<br />

<div class="zadani">
	<p>{cinitel1}*{cinitel2}</p>
</div>

<input bind:value={vysledek2} type="number" />

<button class="tlacitko" on:click={kontrola}>Kontrola</button>

{#if zobrazeniKontroly = 1}

	{#if cinitel1 * cinitel2 == vysledek2}
		<p class="green">správně</p>
	{:else}
		<p class="red">špatně</p>
	{/if}
{/if}

Počet bodů
{body}

<style>
	:global(body) {
		background-color: rgb(255, 255, 255);
	}

	.nadpis1 {
		color: black;
		font-size: 60px;
		font-weight: 400;
	}

	.boxTlacitek {
		display: flex;
	}

	.tlacitko {
		color: black;
		font-size: 30px;
		font-weight: 400;
		width: 25%;
		padding: 15px;
		margin: 5px;
	}

	.blok1 {
		display: flex;
		flex-direction: column;
		color: blue;
		border: 5px solid black;
		background-color: black;
		padding: 0px 20px;
		box-sizing: border-box;
		align-items: center;
		padding-bottom: 20px;
	}

	.green {
		color: green;
	}

	.red {
		color: red;
	}
	.zadani {
		display: flex;
	}
</style>
