<script>

	let todoList = [{text: 'test1', status: true},
					{text: 'test2', status: false},
					{text: 'test3', status: false}
					]

	let newItem = ''

	const handleAdd = () => {
		todoList = [{text: newItem, status: false}, ...todoList]
		newItem = ''
	}

	const handleDelete = (index) => {
		todoList.splice(index, 1)
		todoList = todoList
	}

</script>

<h1>ToDo List Svelte</h1>

<div class="form">

	<input bind:value={newItem} type="text" placeholder="Nueva tarea">
	<button on:click={() => handleAdd()} >Agregar</button>

</div>

<div class="list">
	<br />
	{#each todoList as item, index}
		<div class="item-button">
				<input bind:checked={item.status} type="checkbox" />
				<span class:checked={item.status} >{item.text}</span>
				<button class='delete' on:click={() => handleDelete(index) } >Eliminar</button>	
				<br />
		</div>
	{/each}
</div>


<style>
	.checked {
		text-decoration: line-through;
	}
	h1 {
		text-align: center;
	}
	.form {
		display: flex;
		justify-content: center;
	}
	.list {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 10px;
	}	
	.delete {
		background-color: rgb(196, 34, 34);
		color: #FFF;
		cursor: pointer;
		margin-left: 40px;
	}
</style>