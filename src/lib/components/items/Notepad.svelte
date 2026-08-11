<script>
    import { fade } from 'svelte/transition';
    let {size = 100, placeholder = "Text here", bgcolor = 'palegoldenrod'} = $props();

    let editing = $state(false);
    let text = $state('');

    function startEditing() {
        console.log('editing');
        editing = true;
    }

    function handleKeyDown(event) {
        if (event.key === 'Enter') {
          startEditing();
        }
    }
    function startDragging(event) {
      //TODO: track mouse movement
    }
    /*
    TODO:
    - Max amount of text/lines constrained to note size
    - Stop editing mode when clicking outside the textarea
    - Fix problem where you must click 3 times to start editing
    */
</script>

<div
    in:fade={{ duration: 400 }}
    class="note"
    role="button"
    tabindex="0"
    style="
        width: {size}px;
        height: {size}px;
        left: calc(50vw - {size}px / 2);
        top: calc(50vh - {size}px / 2);
">
    {#if editing}
        <textarea
            bind:value={text}
            style="background-color: {bgcolor};"
        ></textarea>
    {:else}
        <textarea
            class="read-only"
            readonly
            onclick={startEditing}
            onkeydown={handleKeyDown}
            style="background-color: {bgcolor};"
            placeholder={placeholder}
        >{text}</textarea>
    {/if}
</div>

<style>
    .note{
        position: absolute;
        margin: 10px;
    }
    textarea {
        position: absolute;
        width: 100%;
        height: 100%;
        resize: none;
        padding: 6px;
        box-sizing: border-box;
        border-radius: 2.5%;
        overflow: hidden;
        border: none;

    }
    textarea::placeholder {
        color: black;
        opacity: 30%;
    }
    .read-only:focus{
        outline: none;
        box-shadow: none;
    }

</style>
