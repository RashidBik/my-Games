<script>
export let top = 50;
export let left = 150;
export let isHead;
export let direction = "right";


</script>

<div style="left: {left}px; top: {top}px;" class="snake-body {direction}">
    {#if isHead}
        <div id="leftEye" class="eyes"></div>
        <div id="rightEye" class="eyes"></div>
    {/if}
</div>

<style>
    .snake-body {
        background: green;
        border: black 1px solid;
        position: absolute;
        width: 48px;
        height: 48px;
        /* margin: 15px; */
        z-index: 3;
    }

    .eyes {
        position: absolute;
        background: #000;
        border-radius: 50%;
        width: 20%;
        height: 20%;
    }
    #leftEye {
        left: 70%;
        top: 10%;
    }
    #rightEye {
        right: 70%;
        top: 10%;
    }

    .snake-body.up {
        transform: rotate(0deg);
    }
    .snake-body.right {
        transform: rotate(90deg);
    }
    .snake-body.left {
        transform: rotate(270deg);
    }
    .snake-body.down {
        transform: rotate(180deg);
    }

</style>
