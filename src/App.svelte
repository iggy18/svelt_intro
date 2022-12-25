<script>
	import ToDoInputForm from './ToDoInputForm.svelte';
	import ToDoList from './ToDoList.svelte';
	let nameEntered = false;

	let firstName = '';
	let lastName = '';
	
	$: fullName = `${firstName} ${lastName}`;

	function handleSubmit() {
		if (firstName && lastName) {
			nameEntered = true;
		}
	}
</script>

<main>
	{#if nameEntered}
		<h1>Welcome to task manager {fullName}!</h1>
		<ToDoInputForm userName={fullName} />
		<ToDoList />
	{:else}
		<h1>Welcome to task manager!</h1>
		<p>Please enter your name:</p>
		<form on:submit|preventDefault={handleSubmit}>
			<div>
				<input type="text" bind:value={firstName} placeholder="First Name" required/>
			</div>
			<div>
				<input type="text" bind:value={lastName} placeholder="Last Name" required/>
			</div>
			<button on:click={handleSubmit}>Start managing tasks</button>
		</form>
	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 450px;
		margin: 0 auto;
	}
</style>