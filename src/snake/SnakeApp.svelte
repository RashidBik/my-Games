<script>
    // import { localStorageStore } from "@babichjacob/svelte-localstorage/browser";
    import Food from "./Food.svelte";
    import Snake from "./Snake.svelte";
    let foodLeft = 50;
    let foodTop = 200;
    let direction = "right";
    
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

        if (isCollide(newHead,{left: foodLeft, top: foodTop}) ) {
            foodMove();   
            snakeBodies = [...snakeBodies, snakeBodies[snakeBodies.length - 1]];     
        }
        
        if(isGameOver() === true){
            // alert("Game Over");
            resetGame();
            
        }
        
    },200);
    
    function isGameOver() {
        const snakeBodiesNoHead = snakeBodies.slice(1);
        const snakeCollisions = snakeBodiesNoHead.filter(sb =>
        isCollide(sb, snakeBodies[0]));
        
        if (snakeCollisions.length > 0 ) {``
            return true;
        }
        const {top, left} =snakeBodies[0];
        
        if (top >= window.innerHeight - 100 || top < 0 || left < 0 || left >= window.innerWidth) {
            return true;
        }
        
        return false;
    };
    
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
    
    function foodMove() {
        foodTop = Math.floor(Math.random() * 10) * 50;
        foodLeft = Math.floor(Math.random() * 20) * 50;
    };
    
    function resetGame() {
        foodMove();
        direction = 'right';
        snakeBodies = [ 
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
}
resetGame();
$: myScore = (snakeBodies.length - 3) * 5;

// let highScore = localStorageStore('myScore','myScore');

</script>

<main class="bg-red-900">
    <Food {foodLeft} {foodTop}/>
    <Snake {snakeBodies} {direction} />
</main>
<span class="text-4xl text-yellow-400">Your Score: {myScore}</span>
<!-- <span class="text-4xl text-yellow-400">Your Last Score: {highScore}</span> -->

<svelte:window on:keydown={onkeydown} />

<style>
    main {
        border: 5px solid orange;
        width: 100%;
        height: 90%;
    }
</style>