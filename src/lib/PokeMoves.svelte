<script>
    export let pokemon;
    export let method;
    export let version;
    import { Table, TableBody, TableHead, TableHeadCell } from "flowbite-svelte";
    import Move from "./Move.svelte";

    function isRelevant(version_details) {
        if (version_details.version_group.name == version && version_details.move_learn_method.name == method) {
            return true
        }
        return false
    }

    const moves =[];
    function getMoves(moves) {
        const moveList = [];
        for (const move of pokemon.moves ) {
            for (const versionDetails of move.version_group_details) {
                if (isRelevant(versionDetails)) {
                    move.version_group_details = [versionDetails]

                    moveList.push(move)
                    break
                }
            }
        }
        moveList.sort((a,b) => a.version_group_details[0].level_learned_at - b.version_group_details[0].level_learned_at);
        return moveList
    }

</script>

<div>
    <Table striped={true} color="blue">
        <TableHead>
            <TableHeadCell>Lvl</TableHeadCell>
            <TableHeadCell>Name</TableHeadCell>
            <TableHeadCell>Power</TableHeadCell>
            <TableHeadCell>Accuracy</TableHeadCell>
            <TableHeadCell>Type</TableHeadCell>
            <TableHeadCell>Class</TableHeadCell>
        </TableHead>
            <TableBody>
                {#each getMoves(pokemon.moves) as mv }
                    <Move move={mv} versionIndex={0}></Move>


                {/each}
    </TableBody>
    </Table>
</div>