<script>
    export let foodTop;
    export let foodLeft;
</script>

<div class="food" style="left: {foodLeft}px; top: {foodTop}px; ">

</div>

<style>
    .food {
        position: absolute;
        width: 50px;
        height: 50px;
        background: orange;
        border-radius: 50%;
        z-index: 0;

    }
</style>
