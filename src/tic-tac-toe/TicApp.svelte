<script>
let buttons = new Array(9).fill(null);
let result = null;
let turn = 'X';

const winCombination = [
    [0,1,2],
    [3,4,5],
    [6,7,8],
    [0,3,6],
    [1,4,7],
    [2,5,8],
    [0,4,8],
    [2,4,6],
]

const setValue = (i) => {
    buttons[i] = turn;
    buttons = [...buttons];
    turn = turn== 'X'?'O':'X';

    if (!buttons.includes(null)) {
        result = "Match Draw";        
    }else{
        checkWinner()
    }
} 

const checkWinner = () => {
    for (let i = 0; i < winCombination.length; i++) {
        if(buttons[winCombination[i][0]] != null){
            if (buttons[winCombination[i][0]] == buttons[winCombination[i][0]] &&
                buttons[winCombination[i][1]] == buttons[winCombination[i][2]]) {
                result = "Winner: " + buttons[winCombination[i][0]];
                break;  
            }
        }
        
    }
}

const restart = () => {
     buttons = new Array(9).fill(null);
     result = null;
     turn = 'X';
}
</script>

<style>
.tictac {
    width: 300px;
    height: 300px;
    display: flex;
    flex-wrap: wrap;
}

.tictac button {
    width: 100px;
    height: 100px;
    margin: 0px;
    border: 1px solid red;
}
</style>

{#if !result}
    <div class="tictac">
        {#each buttons as  button , i }
            <button on:click={()=>{setValue(i)}}>
                {button}
            </button>
        {/each}
    </div>
{:else}
<div>
{result}
<button on:click={restart}>
    Restart
</button>
</div>
{/if}