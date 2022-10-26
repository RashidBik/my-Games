<script>
    import {getRandomJoke, searchJokes} from './request';
    import Form from "./Form.svelte";
    import Jokes from "./Jokes.svelte";
    import { onMount } from 'svelte';

    let randomJoke;
    let jokes = [];
    let mode = 'loading';
    
onMount(async()=> {
    randomJoke  =  await onRandomJoke();
});

async function onRandomJoke() {
    try {
        mode = 'loading';
        await sleep(500);
        randomJoke = await getRandomJoke();
        await sleep(500);
        mode = 'random';
    } catch (error) {
        alert(error + "There is an error");
    }
};

const onSearch = async (e) => {
    try {
        mode = 'loading';
        await sleep(500);
        jokes = await searchJokes(e.detail)
        await sleep(500);
        mode = 'search';
    } catch (error) {
        console.log(error);
    }
};

const sleep = (delayMs) => new Promise(res => setTimeout(res, delayMs));
</script>

<div>
    <Form on:search={onSearch}/>
    {#if mode === 'random'}
        <Jokes joke={randomJoke} />
    {:else if mode === 'search' && jokes.length > 0}
        {#each jokes as jokeObj (jokeObj.id) }
            <Jokes joke={jokeObj.joke}/>
        {/each}
    {:else if jokes.length === 0}
        <Jokes joke="Jokes On You :)" />
    {/if}
</div>