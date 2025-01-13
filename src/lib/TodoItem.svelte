<script>
    let { todo = $bindable(), onDelete } = $props();
</script>

<div>
    <input type="text" bind:value={todo.name} />
    <input type="checkbox" bind:checked={todo.completed} />
    <label>
        <button onclick={onDelete} >
            Löschen
        </button>
    </label>
</div>