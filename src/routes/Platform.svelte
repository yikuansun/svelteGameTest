<script context="module">
    let current;
</script>

<script>
    export let x = 0;
    export let y = 0;
    export let width = 100;
    export let height = 100;
</script>

<rect width={width} height={height} x={x} y={y} style="fill: green;" />

<svelte:options accessors={true} />