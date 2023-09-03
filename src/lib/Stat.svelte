<script>
    import { Badge, Card } from "flowbite-svelte";
    import { get } from "svelte/store";

    export let stat;

    function getColors(value) {
        if (value < 50) {
            return 'bg-red-800'
        }
        if (value < 70) {
            return 'bg-orange-600'
        }
        if (value < 100) {
            return 'bg-yellow-400'
        }
        if (value < 135) {
            return 'bg-green-500'
        }
        if (value < 150) {
            return 'bg-light-green-500'
        }
        return 'bg-blue-400'
    }
</script>

<div class="columns-2 h-5 p-3 w-full">
    <p class=" text-left left-20 font-bold align-bottom">{stat.stat.name}:</p>
    <div>
    <div style={`width: ${stat.base_stat}px`} class="{getColors(stat.base_stat)} h-fit rounded-xl">
        <p class="font-extrabold">{stat.base_stat}
        </p>
    </div>
    </div>
</div>