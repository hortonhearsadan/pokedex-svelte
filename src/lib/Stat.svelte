<script>
  import { Badge, Card } from "flowbite-svelte";
  import { get } from "svelte/store";

  export let stat;

  function getColors(value) {
    const statColors = {
      50: "bg-[#ff0000]",
      55: "bg-[#ff1800]",
      60: "bg-[#ff2c00]",
      65: "bg-[#ff3200]",
      70: "bg-[#ff6600]",
      75: "bg-[#ff6a00]",
      80: "bg-[#ff9800]",
      85: "bg-[#66ff00]",
      90: "bg-[#ffc000]",
      95: "bg-[#ffe400]",
      100: "bg-[#fffe00]",
      105: "bg-[#f6ff00]",
      110: "bg-[#d8ff00]",
      115: "bg-[#b4ff00]",
      120: "bg-[#9aff00]",
      130: "bg-[#66ff00]",
      140: "bg-[#34ff00]",
      150: "bg-[#02ff2a]",
      160: "bg-[#02ff55]",
      170: "bg-[#02ff7f]",
      180: "bg-[#02ffaa]",
      230: "bg-[#02ffff]",
      500: "bg-[#02ffff]",
    };

    for (const [threshold, color] of Object.entries(statColors)) {
      if (value <= threshold) {
        return color;
      }
    }
  }
</script>

<div class="columns-2 h-5 p-3 w-full">
  <p class=" text-left left-20 font-bold align-bottom">{stat.stat.name}:</p>
  <div>
    <div
      style={`width: ${stat.base_stat}px`}
      class="{getColors(stat.base_stat)} h-fit rounded-md"
    >
      <p class="font-semibold text-left">{stat.base_stat}</p>
    </div>
  </div>
</div>
