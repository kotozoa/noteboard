<script>
    import ColorPicker from './ColorPicker.svelte';
    import SideButton from './SideButton.svelte';

    let { addNote, changeColor, colors} = $props();
</script>

<aside class="side-panel">
    <SideButton onclick={addNote} label="+" ariaLabel="Add note" tooltiptext="Add note" />
    <ColorPicker {changeColor} {colors} />
</aside>

<style>
    .side-panel {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 6px;

        width: 44px;
        padding: 6px;

        border-radius: 10px;
        border-width: 3px;
        border-style: solid;
        border-color: white;
        outline-offset: 3px;
        background-color:#a34365;

        z-index: 100;
    }
</style>
