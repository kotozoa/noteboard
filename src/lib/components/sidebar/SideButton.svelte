<script>
    let {onclick, label = '', color='beige'} = $props();
</script>

<button onclick={onclick} style='background-color: {color};'>{label}</button>

<style>
    button {

        align-self: start;
        width: 80%;
        aspect-ratio: 1 / 1;
        margin: 4px;
        border-radius: 6px;
        border: none;
        cursor: pointer;
    }
</style>
