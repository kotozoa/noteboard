<script>
    import Notepad from '$lib/components/items/Notepad.svelte';

    let { notes, width, height } = $props();
</script>

<div class="notepad-container"
    style="
    width: {width}vw;
    height: {height}vh;
    ">
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
        position: relative;
        background-color: darkslategrey;
        border-radius: 24px;
        width: 80vw;
        height: 80vh;
    }
</style>
