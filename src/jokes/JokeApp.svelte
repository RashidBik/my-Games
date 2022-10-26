<script>
    import {getRandomJoke} from './request';
    import Form from "./Form.svelte";
    import Jokes from "./Jokes.svelte";
    import { onMount } from 'svelte';
let randomJoke;
let mode = 'random';
onMount(async()=> {
    randomJoke  =  await onRandomJoke();
});
async function onRandomJoke() {
    try {
        randomJoke = await getRandomJoke();
    } catch (error) {
        alert(error + "There is an error");
    }
}
</script>

<div>
    <Form />
    <button class="bg-gray-300">randomJoke</button>
    <Jokes />
</div>