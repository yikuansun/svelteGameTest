<script>
    import Platform from "./Platform.svelte";
    import Player from "./Player.svelte";
    import { onMount } from "svelte";

    const gameWidth = 960, gameHeight = 540;

    let playerObject;
    let platforms = [];
    let platformsData = [
        {
            x: 0, y: 480,
            width: 960, height: 60,
        },
        {
            x: 180, y: 420,
            width: 180, height: 60,
        },
        {
            x: 420, y: 360,
            width: 60, height: 60,
        },
        {
            x: 540, y: 300,
            width: 180, height: 60,
        },
    ];

    function tick() {
        playerObject.tick();
    }

    onMount(function() {
        setInterval(tick, 1000 / 60);
    });
</script>

<div style="background-color: deepskyblue; width: {gameWidth}px; height: {gameHeight}px; position: relative;">
    <Player bind:this={playerObject} platforms={platforms}></Player>
    {#each platformsData as plat, i}
        <Platform x={plat.x} y={plat.y} width={plat.width} height={plat.height} bind:this={platforms[i]}></Platform>
    {/each}
</div>