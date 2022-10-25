<script>
    let grid = [];
    let row = 10;
    let col = 10;
    let bombs = 10;
    for(let i =0; i < row; i++){
        grid[i] = new Array(col);
        for (let j = 0; j < col; j++) {
            grid[i][j] = {
                bombs: false,
                revealed: false,
                distance: 0
            }
            
        }
    }
</script>