<template>
	<div class="card my-3" v-if="total">
		<ul class="list-group overflow-hidden">
			<div class="d-flex justify-content-between align-items-center" v-for="(todo, index) in todos" :key="index">
				<li class="list-group-item w-100 border-0">
					<span v-if="todo.isDone">
						<del>{{ todo.activity }}</del>
					</span>
					<span v-else>{{ todo.activity }}</span>
				</li>

				<button type="button" class="btn btn-sm btn-success mx-1" @click="doneToDo(index)">
					<i class="bi bi-check"></i>
				</button>
				<button type="button" class="btn btn-sm btn-danger mx-1" @click="deleteToDo(index)">
					<i class="bi bi-x"></i>
				</button>
			</div>
		</ul>
	</div>
</template>

<script>
export default {
	props: {
		todos: {
			type: Array,
			default: [],
		},
		total: Number,
	},
	setup(props, { emit }) {
		const doneToDo = (index) => {
			emit('doneToDo', index)
		}

		const deleteToDo = (index) => {
			emit('deleteToDo', index)
		}

		return { doneToDo, deleteToDo}
	}
}
</script>