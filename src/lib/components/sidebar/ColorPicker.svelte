<script>
    import SideButton from "./SideButton.svelte";

    let {changeColor, colors} = $props();

    /*
    TODO
    - Add a current color selection indicator
    - Either a simple border or a little pointer arrow
    - Animate with sliding (?)
    */
</script>

<SideButton onclick={() => changeColor('random')} label='?' ariaLabel="Random color" />
{#each colors as color}
    <SideButton onclick={() => changeColor(color)} label='' {color} ariaLabel={`${color}`} />
{/each}
