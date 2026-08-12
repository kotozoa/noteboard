<script>
    import { fade } from 'svelte/transition';
    let {
      x = 0,
      y = 0,
      size = 100,
      placeholder = "New note",
      bgcolor = 'palegoldenrod',
    } = $props();

    // Movement logic
    let position = $state({ x, y });
    let moving = false;

    function onMouseDown() {
        if (editing) return;
        moving = true;
    }

   	function onMouseUp() {
		moving = false;
	}

    function onMouseMove(e) {
        if (!moving) return;
        position.x += e.movementX;
        position.y += e.movementY;
    }


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

    /*
    TODO:
    - Max amount of text/lines constrained to note size
    - Make caret blink again
    - Caret doesnt appear when editing when double clicked, but appears when clicked again
    - Cursor to move when dragging or hovering
    - Fix highlight text when dragging and no drag when clicked once
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
        left: {position.x}px;
        top: {position.y}px;
">
    <textarea
        bind:this={textarea}
        bind:value={text}
        readonly={!editing}
        ondblclick={startEditing}
        onmousedown={onMouseDown}
        onblur={stopEditing}
        placeholder={placeholder}
        style="background-color: {bgcolor};"
    ></textarea>
</div>

<svelte:window on:mouseup={onMouseUp} on:mousemove={onMouseMove} />

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
    textarea:focus-visible {
        outline: none;
        box-shadow: 0 0 0 2px white;
    }

</style>
