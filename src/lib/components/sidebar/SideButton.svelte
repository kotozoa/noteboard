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
        border-radius: 6px;
        padding: 4px;

        background-color: black;
        color: #fff;
        text-align: center;
        white-space: nowrap;
        overflow: hidden;
        z-index: 1;

        position: absolute;
        left: calc(100% + 4px);
        top: 50%;
        transform: translateY(-50%);
    }

    button:hover .tooltip {
        visibility: visible;
    }

    button {
        position: relative;

        width: 98%;
        aspect-ratio: 1 / 1;
        border-radius: 6px;
        box-sizing: border-box;
        border: none;
        cursor: pointer;
    }

    button:hover{
        border-color: #a34365;
        border-width: 3px;
        border-style: solid;
    }

</style>
