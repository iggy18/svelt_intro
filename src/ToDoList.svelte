<script>

    import { toDoItems} from './store.js';
    import { fade, scale } from "svelte/transition"
    
    function removeFromList(index) {
        $toDoItems.splice(index, 1)
        $toDoItems = $toDoItems
    }

</script>

{#each $toDoItems as item, index}
    <div class="toDoItems" in:scale out:fade={{duration: 500}}>
        <input bind:checked={item.status} type='checkbox'>
        <span class:checked={item.status}>{item.text}</span>
        <button on:click={() => removeFromList(index)}>Remove</button>
    </div>
{/each}

<style>
    .checked {
        text-decoration: line-through;
    }
    .toDoItems {
        display: flex;
        align-items: center;
    }

</style>