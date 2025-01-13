<script>
	import TodoItem from "$lib/TodoItem.svelte";
	let todos = $state([
		{
			name: 'Einkaufen',
			completed: false
		}
	]);
	let completedTodos = $derived(todos.filter(t => t.completed).length);
	const deleteTodo = (index) => {
        todos = todos.filter((_, i) => i !== index);
    };
	$inspect(todos);
</script>

	<main>
		<div class="container">
			<h1>Todo App</h1>
			<input
				type="text"
				placeholder="Neues Todo eingeben"
				onkeydown={(e) => {
					if (e.key === 'Enter' && e.target.value.trim()) {
						todos.push({
							completed: false,
							name: e.currentTarget.value
						});
						e.currentTarget.value = '';
					}
				}}
			/>

			{#each todos, i}
				<TodoItem bind:todo={todos[i]} onDelete={() => deleteTodo(i)}/>
			{/each}

			<p>Abgeschlossene Todos: {(console.log('clicked'), completedTodos)}</p>
		</div>
	</main>

<style>
	:root {
        font-family: Arial, Helvetica, sans-serif;
        background-color: lightgrey;
    }

    main {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

    .container {
        background-color: lightblue;
        padding: 20px;
        border-radius: 6px;
        border: 1px solid;
        box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.2);
    }
</style>