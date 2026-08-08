<script>
    import ColorPicker from './ColorPicker.svelte';
    import SideButton from './SideButton.svelte';

    let { addNote, changeColor, colors } = $props();
</script>

<aside class="side-panel">
    <SideButton onclick={addNote} label="+" />
    <ColorPicker changeColor={changeColor} {colors} />
</aside>

<style>
    .side-panel {
        display: flex;
        justify-content: center;
        flex-direction: column;
        flex-wrap: wrap;
        width: 50px;
        margin: 8px;
        border-radius: 6px;
        background-color: dimgrey;
        position: absolute;
        top: 0;
        left: 0;
        z-index: 100;
    }
</style>
