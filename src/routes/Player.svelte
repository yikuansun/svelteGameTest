<script context="module">
    let current;
</script>

<script>
    import { onMount } from "svelte";

    export let x = 20;
    export let y = 250;
    export let velocityX = 0;
    export let velocityY = 0;
    export let width = 60;
    export let height = 60;
    export let platforms = [];

    let keysDown = {};

    onMount(function() {
        window.addEventListener("keydown", function(e) {
            keysDown[e.key] = true;
        });
        window.addEventListener("keyup", function(e) {
            keysDown[e.key] = false;
        });
    });

    function collidingWidth(rect2) {
        return (
            x < rect2.x + rect2.width &&
            x + width > rect2.x &&
            y < rect2.y + rect2.height &&
            y + height > rect2.y
        );
    }

    function touchingGround() {
        for (let plat of platforms) {
            if (collidingWidth(plat)) return true;
        }
        return false;
    }

    export let tick = () => {
        if (touchingGround()) velocityY = 0;
        else velocityY++;

        if (keysDown["ArrowRight"]) velocityX = 5;
        else if (keysDown["ArrowLeft"]) velocityX = -5;
        else velocityX = 0;

        if (!touchingGround()) {
            x += velocityX;
            if (touchingGround()) {
                x -= velocityX;
                velocityX = 0;
            }
        }
        else x += velocityX;
        if (!touchingGround()) {
            y += velocityY;
            if (touchingGround()) {
                y -= velocityY;
                if (keysDown["ArrowUp"] && velocityY >= 0) velocityY = -15;
                else velocityY = 0;
            }
        }
        else y += velocityY;
    };
</script>

<div
    style="
        position: absolute;
        width: {width}px;
        height: {height}px;
        top: {y}px;
        left: {x}px;
        background-color: darkblue;
        border-radius: 15px;
        border: 5px solid darkslateblue;
        box-sizing: border-box;
    "
></div>

<svelte:options accessors={true} />