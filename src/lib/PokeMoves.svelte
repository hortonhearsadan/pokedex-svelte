<script>
    export let pokemon;
    export let method;
    export let version;
    import Move from "./Move.svelte";

    function isRelevant(version_details) {
        if (version_details.version_group.name == version && version_details.move_learn_method.name == method) {
            return true
        }
        return false
    }


</script>

<div>
    {#each pokemon.moves as mv }
        {#each mv.version_group_details as version}
            {#if isRelevant(version)} 
                <Move move={mv}></Move>
            {/if}

        {/each}
    <!-- {JSON.stringify(mv.version_group_details)} -->
    {/each}
</div>