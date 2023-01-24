<style>
	.checked {
		text-decoration: line-through;
	}
</style>

<script lang="ts">
	let newItem = ''

	type TodoType = {
		text: string
		status: boolean
	}

	let todoList: TodoType[] = [
		{ text: 'first todo', status: true },
		{ text: 'second todo', status: false }
	]

	const addToList = () => {
		todoList = [...todoList, { text: newItem, status: false }]
		newItem = ''
	}

	const removeFromList = (index: number) => {
		todoList.splice(index, 1)
		todoList = todoList
	}

	$: todoListCompleteCount = todoList.filter((todo) => todo.status).length
	$: todoListCount = todoList.length
</script>

<form on:submit={addToList}>
	<div class="p-4">
		<input
			bind:value={newItem}
			type="text"
			placeholder="new todo item"
			required
			class="rounded-lg border border-gray-300 bg-gray-50 p-2.5 text-sm text-gray-900 focus:border-blue-500 focus:ring-blue-500 dark:border-gray-600 dark:bg-gray-700 dark:text-white dark:placeholder-gray-400 dark:focus:border-blue-500 dark:focus:ring-blue-500"
		/>
		<button
			type="submit"
			class="w-full rounded-lg bg-blue-700 px-5 py-2.5 text-center text-sm font-medium text-white hover:bg-blue-800 focus:outline-none focus:ring-4 focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800 sm:w-auto"
		>
			Add
		</button>
	</div>
</form>

<main class="max-w mx-auto px-4">
	<div class="pt-1 pb-4">
		{#each todoList as item, index}
			<div class="flex items-center">
				<input
					bind:checked={item.status}
					id={`checked-checkbox-${index}`}
					type="checkbox"
					value=""
					class="dark:focus:ring-blue-600`} h-4 w-4 rounded border-gray-300 bg-gray-100 text-blue-600 focus:ring-2 focus:ring-blue-500 dark:border-gray-600 dark:bg-gray-700 dark:ring-offset-gray-800"
				/>
				<label
					for={`checked-checkbox-${index}`}
					class={`${
						item.status && 'checked'
					} ml-2 text-sm font-medium text-gray-900 dark:text-gray-300`}
				>
					{item.text}
				</label>
				<button on:click={() => removeFromList(index)}>💥</button>
			</div>
		{:else}
			<span>No tasks</span>
		{/each}
	</div>

	<p class="text-blue-600">tasks {todoListCompleteCount}/{todoListCount}</p>
</main>
