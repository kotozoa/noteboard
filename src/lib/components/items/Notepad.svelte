<script>
    import { fade } from 'svelte/transition';
    let {size = 100, text = "Text here", bgcolor = 'palegoldenrod'} = $props();

    /*
    TODO:
    - Max amount of text/lines constrained to note size
    */
</script>

<div in:fade={{ duration: 400 }} class="note" style="
    min-width: {size}px;
    min-height: {size}px;
    max-width: {size}px;
    max-height: {size}px;
    left: calc(50vw - {size}px / 2);
    top: calc(50vh - {size}px / 2);
">
    <textarea style="background-color: {bgcolor};"
        placeholder={text}></textarea>
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

</style>
