<script>
    import Notepad from '$lib/components/items/Notepad.svelte';

    let { notes } = $props();
</script>

<div class="notepad-container">
    {#each notes as note}
        <Notepad
            x={note.x}
            y={note.y}
            size={note.size}
            placeholder={note.placeholder}
            bgcolor={note.bgcolor}
        />
    {/each}
</div>

<style>
    .notepad-container {
        background-color: black;
        width: 90vw;
        height: 90vh;
    }
</style>
