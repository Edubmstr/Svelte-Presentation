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

<style>
    div {
        margin: 8px 0;
    }
    button {
        background-color: coral;
        border-radius:  6px;
        border: none;
        padding: 5px;
    }
</style>