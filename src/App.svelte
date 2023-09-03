<script>
	import PokeMoves from './lib/PokeMoves.svelte';
import PokeStats from './lib/PokeStats.svelte';
import PokeSummary from './lib/PokeSummary.svelte'
	
	let selectedPokemon = '';
	let pokemon_name = '';

	let pokepromise;

	async function getPokemon(url) {
		const res = await fetch(url);
		return await res.json();
	}
	async function handleKeypress(e) {
      if (e.key === "Enter") {
          selectedPokemon = pokemon_name
		  pokepromise = getPokemon("https://pokeapi.co/api/v2/pokemon/".concat(pokemon_name.toLowerCase()));
      }
    }
</script>

<h1 class="align-text-top ">
	Pokédex
</h1>

<div>
	<div>
		<input bind:value={pokemon_name} placeholder="enter pokemon name" on:keypress={handleKeypress} class="h-6 content-center top" />
	</div>
	{#await pokepromise}{:then pokemon} 
		
	<div class="content-center">
		{#if selectedPokemon}

			<PokeSummary pokemon={pokemon}/>
			<PokeStats pokemon={pokemon}/>
			<PokeMoves pokemon={pokemon} method= "level-up" version="scarlet-violet"/>
		{:else}
			Select a pokemon
		{/if}
</div>
{:catch error}
	Something went Wrong!

{/await}
</div>

