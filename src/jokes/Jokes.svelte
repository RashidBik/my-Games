<script>
    import Transation from "./Transation.svelte";
    
    export let joke;
</script>

<Transation>
    <div>
        {joke}
        Jokes......haha
        <button class="bg-gray-300">randomJoke</button>
    </div>
</Transation>