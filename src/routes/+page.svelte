<script>
    import Player from "./Player.svelte";
    import { onMount } from "svelte";

    const gameWidth = 960, gameHeight = 540;

    let playerObject;

    function tick() {
        playerObject.tick();
    }

    onMount(function() {
        setInterval(tick, 1000 / 60);
    });
</script>

<svg width={gameWidth} height={gameHeight} style="background-color: deepskyblue;">
    <Player bind:this={playerObject}></Player>
</svg>