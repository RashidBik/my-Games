<script>
    import { createEventDispatcher } from "svelte";

let term = '';
$: canSubmit = term.length > 0;
const dispatch = createEventDispatcher();
function onSearch (e) {
    if (canSubmit) {
        
        dispatch('search', term);
    }
}
</script>

<form on:submit|preventDefault={onSearch}>
    <input type="search" bind:value={term} >
<label for="search">Search</label>
<button type="submit">Search</button>
</form>