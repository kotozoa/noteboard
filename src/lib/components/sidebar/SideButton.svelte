<script>
    let {onclick, label = ''} = $props();
</script>

<button onclick={onclick}>{label}</button>

<style>
    button {

        align-self: start;
        width: 80%;
        aspect-ratio: 1 / 1;
        margin: 4px;
        border-radius: 6px;
        border: none;
        background-color: beige;
        cursor: pointer;
    }
</style>
