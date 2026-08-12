<script>
    import ColorPicker from './ColorPicker.svelte';
    import SideButton from './SideButton.svelte';

    let { addNote, changeColor, colors} = $props();
</script>

<aside class="side-panel">
    <SideButton onclick={addNote} label="+" />
    <SideButton onclick={() => {}} label="-" />

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
        margin: 16px;

        border-radius: 10px;
        border-width: 3px;
        border-style: solid;
        border-color: white;
        outline-offset: 3px;
        background-color:#a34365;
        position: fixed;
        top: 0;
        left: 0;

        z-index: 100;
    }
</style>
