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
">
    <textarea style="background-color: {bgcolor};"
        placeholder={text}></textarea>
</div>

<style>
    .note{
        padding: 10px
    }
    textarea {
        width: 100%;
        height: 100%;
        resize: none;
        border-radius: 2.5%;
        overflow: hidden;
        border: none;
    }
    textarea::placeholder {
        color: black;
        opacity: 30%;
    }

</style>
