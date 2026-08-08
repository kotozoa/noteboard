<script>
    import Notepad from './Notepad.svelte';
    import SidePanel from '$lib/components/sidebar/SidePanel.svelte'
    // Handle colors
    let selectedColor = $state('palegoldenrod');

    function changeColor(color) {
        selectedColor = color;
    }
    // Handle notes
    let notes = $state([{ size: 100, text: "Sample Note", bgcolor: "palegoldenrod" }]);

    function addNote(){
        notes.push({
          size: 100,
          text: "New Note",
          bgcolor: selectedColor
        });
    }
</script>

<SidePanel {addNote} {changeColor} />

<div class="notepad-container">
    {#each notes as note}
        <Notepad
            size={note.size}
            text={note.text}
            bgcolor={note.bgcolor}
        />
    {/each}
</div>

<style>
    :global(html, body) {
      margin: 0;
      padding: 0;
      height: 100%;
      overflow: hidden;
    }
    .notepad-container {
        background-color: black;
        width: 100vw;
        height: 100vh;
        display: flex;
        align-content: flex-start;
        flex-direction: column;
        flex-wrap: wrap;
    }
</style>
