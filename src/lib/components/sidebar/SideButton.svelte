<script>
    let {onclick, label = '', ariaLabel = '', color='beige'} = $props();
</script>

<button {onclick} style='background-color: {color};' aria-label={ariaLabel}>{label}</button>

<style>
    button {
        width: 98%;
        aspect-ratio: 1 / 1;
        border-radius: 6px;
        border: none;
        cursor: pointer;
    }
    button:hover{
        border-color: #a34365;
        border-width: 3px;
        border-style: solid;
    }
</style>
