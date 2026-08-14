<script>
    let {onclick, label = '', ariaLabel = '', color='beige', tooltiptext = ''} = $props();
</script>

<button {onclick} style='background-color: {color};' aria-label={ariaLabel}>
    {label}
    <span class='tooltip'>
        {tooltiptext}
    </span>
</button>

<style>
    .tooltip {
        visibility: hidden;
        width: auto;
        background-color: black;
        color: #fff;
        text-align: center;
        border-radius: 6px;
        padding: 4px;
        position: absolute;
        z-index: 1;
    }

    button:hover .tooltip {
        visibility: visible;
    }

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
