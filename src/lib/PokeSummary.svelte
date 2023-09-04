
<script>
  export let pokemon;
  import TypeBadge from "./TypeBadge.svelte";



</script>

<div>
    <h2 class="font-bold object-center mx-auto">{pokemon.name}</h2>
    <img src={pokemon.sprites.front_default} alt={pokemon.name} class='mx-auto object-center w-100% center'/>
    {#each pokemon.types as type_}
      <TypeBadge type={type_.type.name}/>
    {/each}
    <!-- <h3>{JSON.stringify(pokemon)}</h3> -->
</div>