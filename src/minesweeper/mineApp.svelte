<script>
    let grid = [];
    let row = 10;
    let col = 10;
    let bombs = 10;
    for(let i =0; i < row; i++){
        grid[i] = new Array(col);
        for (let j = 0; j < col; j++) {
            grid[i][j] = {
                bomb: false,
                revealed: false,
                distance: 0
            }
            
        }
    }

    for (let i = 0; i < bombs; i++) {
        let x = Math.floor(Math.random()*row);
        let y = Math.floor(Math.random()*col);
        if (grid[x][y].bomb) {
            i--;
            continue;
        }
        grid[x][y].bomb = true;
                
    }

    function countDistance(i, j) {
        if (grid[i][j].bomb) {
            grid[i][j].distance = -1
            return;

        }
        let count = 0 ;
        for (let x = 0; x < 1; x++) {
            for (let y = 0; y <= 1; y++) {
                try {
                    if (grid[x+i][j+j].bomb) {
                        count++;
                    }
                } catch (error) {
                    console.log(error);
                }
            }
            
        }
        grid[i][j].distance = count;
    }
</script>

<style>
    .game {
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 400px;
        height: 400px;
        display: flex;
        flex-wrap: wrap;
    }

    .game > div {
        width: 10%;
        height: 10%;
        text-align: center;
        line-height: 40px;
        border: 1px solid #111;
        box-sizing: border-box;
        cursor: pointer;
    }
    .game > div.bomb:before{
        content: "";
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 20px;
        height: 20px;
        background: #111;
        /* border: 1px solid black; */
        border-radius: 50%;
    }
</style>

<div class="game">
    {#each grid as row, i}
        {#each row as box}
            <div class:bomb={box.bomb}>
                {i}{j}
            </div>
        {/each}
    {/each}
</div>