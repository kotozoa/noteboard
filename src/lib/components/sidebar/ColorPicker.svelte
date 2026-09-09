<script>
    import SideButton from "./SideButton.svelte";

    let {changeColor, colors, selectedColor} = $props();
</script>

<SideButton
    onclick={() => changeColor('random')}
    label='?'
    ariaLabel="Random color"
    tooltiptext="Random color"
    active={true}
/>

{#each colors as color}
    <SideButton
        onclick={() => changeColor(color)}
        label=''
        {color}
        ariaLabel={`${color}`}
        tooltiptext={`${color}`}
        active={selectedColor === color}
    />
{/each}
