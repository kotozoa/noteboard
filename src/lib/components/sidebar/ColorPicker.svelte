<script>
    import SideButton from "./SideButton.svelte";

    let {changeColor, colors} = $props();

</script>

<SideButton onclick={() => changeColor('random')} label='?'/>
{#each colors as color}
    <SideButton onclick={() => changeColor(color)} label='' color={color}/>
{/each}
