<script>
export let pokemon;
import Stat from "./Stat.svelte"

function getBST(stats) {
    return stats.reduce((a,b) => a + b.base_stat,0 )
}
</script>

<div >
    <div>
    {#each pokemon.stats as stat}
    <Stat stat={stat}></Stat>
    {/each}
</div>
    <div class="font-bold text-left left-0 p-5">BST: {getBST(pokemon.stats)}</div> 
</div>