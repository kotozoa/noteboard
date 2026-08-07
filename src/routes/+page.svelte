<script>
    import Notepad from './Notepad.svelte';

    // Default colors
    let selectedColor = $state('random');
    let colors = ['random', 'palegoldenrod', 'palevioletred', 'paleturquoise'];

    // Handle notes
    let notes = $state([{ size: 100, padding: 5, text: "Sample Note", bgcolor: "palegoldenrod" }]);

    function addNote(){
      if (selectedColor === 'random') {
        notes.push({
          size: 100,
          padding: 5,
          text: "New Note",
          bgcolor: colors[Math.floor(Math.random() * colors.length) + 1]
        });
      } else {
        notes.push({
          size: 100,
          padding: 5,
          text: "New Note",
          bgcolor: selectedColor
        });
      }
    }
</script>

<div class="notepad-container">
    {#each notes as note}
        <Notepad size={note.size} text={note.text} bgcolor={note.bgcolor}/>
    {/each}
</div>

<div class="sidenav">
    <button onclick={addNote}>Add Note</button>
    <form>
        <select bind:value={selectedColor}>
            {#each colors as color}
                <option value={color}>{color}</option>
            {/each}
        </select>
    </form>
</div>

<style>
    :global(html, body) {
      margin: 0;
      padding: 0;
      height: 100%;
      overflow: hidden;
    }
    .sidenav {
        position: fixed;
        top: 0;
        left: 0;
        width: 200px;
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
