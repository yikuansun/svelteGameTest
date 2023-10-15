<script context="module">
    let current;
</script>

<script>
    export let x = 0;
    export let y = 0;
    export let width = 100;
    export let height = 100;
</script>


<div
    style="
        position: absolute;
        width: {width}px;
        height: {height}px;
        top: {y}px;
        left: {x}px;
        background-color: green;
    "
></div>

<svelte:options accessors={true} />