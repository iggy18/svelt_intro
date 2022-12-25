<script>
    import { toDoItems } from "./store.js";
    import { onMount } from "svelte"

    export let userName;
    let newItem = '';
    let newItemInputForm = null;

    onMount(() => {
        newItemInputForm.focus();
    })

    function addToList() {
        $toDoItems = [...$toDoItems, {text: newItem, status: false}]
    newItem = ""
    }

</script>
<div class="add-component">
    <input bind:value={newItem} bind:this={newItemInputForm} type="text" placeholder="Add a new task">
    <button on:click={addToList}>Add</button>
</div>

<h3> {userName}'s task list: </h3>

<style>
    .add-component {
        background-color: #6b6b6b;
    }
</style>

