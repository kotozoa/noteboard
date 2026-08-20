<script>
    import Notepad from '$lib/components/items/Notepad.svelte';
    import NoteArea from '$lib/components/items/NoteArea.svelte';
    import SidePanel from '$lib/components/sidebar/SidePanel.svelte'

    // Handle colors
    let colors = ['palegoldenrod', 'palevioletred', 'paleturquoise'];
    let selectedColor = $state('random');

    function changeColor(color) {
        selectedColor = color;
        //console.log('Selected color: ', selectedColor)
    }

    // Handle notes
    let notes = $state([{
      x: 200,
      y: 200,
      size: 100,
      placeholder: "Sample note",
      bgcolor: "palegoldenrod",
    }]);

    function addNote(){
        if (selectedColor === 'random'){
            notes.push({
                x: 0,
                y: 0,
                size: 100,
                placeholder: "New Note",
                bgcolor: colors[Math.floor(Math.random() * colors.length)]
            });
        }
        else{
            notes.push({
                x: 0,
                y: 0,
                size: 100,
                placeholder: "New Note",
                bgcolor: selectedColor
            });
        }
    }
    /* TODO:
    - Change function to addnote to the center of note container and a small random x,y offset for visual variety
    - completely rehaul style, make more visually unique
      - custom (dynamic?) background
      - notes can be opaque/frosted glass-like with colors more in line with a theme
      - darker theme with cold colors?
      - side panel styled with a similar idea
      - think of page layout/balancing ui elements

    */

    /*
    let noteCount = $state(notes.length);
    $effect(() => {
        noteCount = notes.length;
    });*/
</script>

<div class="editor">
    <SidePanel {addNote} {changeColor} {colors} {selectedColor}/>
    <NoteArea {notes}/>
</div>

<style>
    :global(html, body) {
      margin: 0;
      padding: 0;
      height: 100%;
      overflow: hidden;
      background-color: black;
    }
    .editor {
        width: 100%;
        height: 100%;
        max-width: 100vw;
        max-height: 100vh;
        position: absolute;
        top: 0;
        left: 0;

        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;

        padding: 20px;
        gap: 20px;
        box-sizing: border-box;
        background-color:grey;
    }
</style>
