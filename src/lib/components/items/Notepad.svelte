<script>
    import { fade } from 'svelte/transition';
    let {size = 100, placeholder = "New note", bgcolor = 'palegoldenrod'} = $props();

    // Textarea states
    let textarea;
    let text = $state('');
    let editing = $state(false);

    function startEditing() {
        editing = true;
        setTimeout(() => textarea?.focus());
    }

    function stopEditing() {
        editing = false;
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
    - Make caret blink again
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
    <textarea
        bind:this={textarea}
        bind:value={text}
        readonly={!editing}
        ondblclick={startEditing}
        onblur={stopEditing}
        placeholder={placeholder}
        style="background-color: {bgcolor};"
    ></textarea>
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
    textarea:read-only{
        outline: none;
        box-shadow: none;
        caret-color: transparent;
    }

</style>
