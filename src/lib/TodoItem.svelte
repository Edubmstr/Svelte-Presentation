<script>
    let { todo = $bindable() } = $props();
</script>

<div>
    <input type="text" bind:value={todo.name} />
    <input type="checkbox" bind:checked={todo.completed} />
</div>