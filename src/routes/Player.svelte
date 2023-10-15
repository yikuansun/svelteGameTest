<script context="module">
    let current;
</script>

<script>
    export let x = 0;
    export let y = 0;
    export let velocityX = 0;
    export let velocityY = 0;
    export let width = 50;
    export let height = 50;

    let keysDown = {};

    window.addEventListener("keydown", function(e) {
        keysDown[e.key] = true;
    });
    window.addEventListener("keyup", function(e) {
        keysDown[e.key] = false;
    });

    export let tick = () => {
        if (keysDown["ArrowRight"]) x++;
        if (keysDown["ArrowLeft"]) x--;
        if (keysDown["ArrowDown"]) y++;
        if (keysDown["ArrowUp"]) y--;
    };
</script>

<rect width={width} height={height} x={x} y={y} style="fill: navyblue;" rx={10} ry={10} />

<svelte:options accessors={true} />