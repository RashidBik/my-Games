<script>
    import Food from "./Food.svelte";
    import Snake from "./Snake.svelte";

    let foodLeft = 50;
    let foodTop = 200;
    let direction;

    let snakeBodies = [ 
        {
            left: 100,
            top: 0,
        },
        {
            left: 50,
            top: 0,
        },
        {
            left: 0,
            top: 0,
        },
    ];

    function isCollide(a, b){
        return !(
            a.top < b.top || 
            a.top > b.top ||
            a.left < b.left ||
            a.left > b.left
        );
    };

    function getDirectionFromKeyCode(keyCode){
        if (keyCode === 38) {
            return "up";
        } else if (keyCode === 39){
            return "right";
        }else if (keyCode === 37){
            return "left";
        }else if (keyCode === 40){
            return "down";
        }
        return false;
    };

    function onkeydown(e) {
        const newDirection = getDirectionFromKeyCode(e.keyCode);
        if (newDirection) {
            direction = newDirection;
        }
    };

    setInterval(() => {
        snakeBodies.pop();
        let {left, top} = snakeBodies[0];
            
        if (direction === 'up') {
            top -= 50;
        }else if (direction === 'down') {
            top += 50;
        } else if (direction === 'left' ) {
            left -= 50;
        } else if (direction === 'right' ) {
            left += 50;
        }
        const newHead = {left, top};
        snakeBodies = [newHead, ...snakeBodies];

    },200);
</script>

<main>
    <Food {foodLeft} {foodTop}/>
    <Snake {snakeBodies} {direction} />

</main>
<svelte:window on:keydown={onkeydown} />

<style>
    main {
        background: rgb(178, 176, 176);
        width: 1000px;
        height: 600px;
    }
</style>