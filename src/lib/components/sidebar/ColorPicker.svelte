<script>
    import SideButton from "./SideButton.svelte";

    let {changeColor} = $props();

    // Default colors
    let colors = ['palegoldenrod', 'palevioletred', 'paleturquoise'];

</script>

{#each colors as color}
    <SideButton onclick={() => changeColor(color)} label={color}/>
{/each}
