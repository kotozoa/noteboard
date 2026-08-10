<script>
    import Notepad from '$lib/components/items/Notepad.svelte';
    import SidePanel from '$lib/components/sidebar/SidePanel.svelte'

    let states = ['select', 'edit', 'delete'];

    // Operations
    function selectNote() {
    }
    function editNote() {

    }
    function deleteNote() {

    }

    // Handle colors
    let colors = ['palegoldenrod', 'palevioletred', 'paleturquoise'];
    let selectedColor = $state('random');

    function changeColor(color) {
        selectedColor = color;
    }
    // Handle notes
    let notes = $state([{ size: 100, text: "Sample Note", bgcolor: "palegoldenrod" }]);

    /* TODO:
    - Change function to addnote to the center of note container and a small random x,y offset for visual variety
    - completely rehaul style, make more visually unique
      - custom (dynamic?) background
      - notes can be opaque/frosted glass-like with colors more in line with a theme
      - darker theme with cold colors?
      - side panel styled with a similar idea
      - think of page layout/balancing ui elements

    */
    function addNote(){
        if (selectedColor === 'random'){
            notes.push({
                size: 100,
                text: "New Note",
                bgcolor: colors[Math.floor(Math.random() * colors.length)]
            });
        }
        else{
            notes.push({
                size: 100,
                text: "New Note",
                bgcolor: selectedColor
            });
        }
    }
</script>

<SidePanel {addNote} {changeColor} {colors} {selectNote} {editNote} {deleteNote} />

<!-- TODO: Change container to allow notes to move anywhere within the container-->
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
    }
</style>
