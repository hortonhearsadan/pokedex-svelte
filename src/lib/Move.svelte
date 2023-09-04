<script>
    export let move;
    export let versionIndex;
    let movePromise ;

    import { TableBodyCell, TableBodyRow } from 'flowbite-svelte';
    import physical from '../assets/physical-attack.png';
    import special from '../assets/special-attack.png';
    import status from '../assets/status-move.png';
    import TypeBadge from './TypeBadge.svelte';

    async function getMove(url) {
        const res = await fetch(url);
        return res.json()

    }

    if (move != undefined) {
        movePromise = getMove(move.move.url)
    }

    function getDamageClassImage(damageClass) {
        if (damageClass == "physical") {
            return physical
        }
        if (damageClass == "special") {
            return special 
        }
        if (damageClass == "status") {
            return status
        }
    } 

    function parseName(name) {
        return name.replace("-"," ")
    }


    function parseValue(value) {
        if (value == null) {
            return "--"
        }
        return value
    }

</script>
    
<TableBodyRow class="h-9 p-3 w-full">

    {#await movePromise}
        
    {:then moveDetails} 
        <TableBodyCell>{move.version_group_details[versionIndex].level_learned_at}</TableBodyCell>
        <TableBodyCell>{parseName(move.move.name)}</TableBodyCell>
        <TableBodyCell>{parseValue(moveDetails.power)}</TableBodyCell>
        <TableBodyCell>{parseValue(moveDetails.accuracy)}</TableBodyCell>
        <TableBodyCell><TypeBadge type={moveDetails.type.name}/></TableBodyCell>
        <TableBodyCell>
            <div>
                <img src={getDamageClassImage(moveDetails.damage_class.name)}/>
            </div>
        </TableBodyCell>
    {/await}
    <!-- <div>{JSON.stringify(move.version_group_details)}</div> -->
        
</TableBodyRow>