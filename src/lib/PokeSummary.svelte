
<script>
  export let pokemon;
  import { Badge } from 'flowbite-svelte';

  const bgClasses = {
        normal: 'bg-normal',
        fire: 'bg-fire',
        water: 'bg-water',
        electric: 'bg-electric',
        grass: 'bg-grass',
        ice: 'bg-ice',
        fighting: 'bg-fighting',
        poison: 'bg-poison',
        ground: 'bg-ground',
        flying: 'bg-flying',
        psychic: 'bg-psychic',
        bug: 'bg-bug',
        rock: 'bg-rock',
        ghost: 'bg-ghost',
        dragon: 'bg-dragon',
        dark: 'bg-dark',
        steel: 'bg-steel',
        fairy: 'bg-fairy',
    };

</script>

<div>
    <h2 class="font-bold object-center mx-auto">{pokemon.name}</h2>
    <img src={pokemon.sprites.front_default} alt={pokemon.name} class='mx-auto object-center w-100% center'/>
    {#each pokemon.types as type_}
    <Badge class={`${bgClasses[type_.type.name]}`}>{type_.type.name}</Badge>
    {/each}
    <!-- <h3>{JSON.stringify(pokemon)}</h3> -->
</div>