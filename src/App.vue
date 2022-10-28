<template>
	<div class="container">
		<div class="card">
			<div class="card-body">
				<h5 class="card-title text-center">Simple Todo</h5>

				<div class="input-group mt-3">
					<input type="text" class="form-control" placeholder="Type here..." v-model="todo" @keyup.enter="addTodo()">
					<button class="btn btn-primary" type="button" id="button-addon2" @click="addTodo()">Add</button>
				</div>
			</div>
		</div>

		<list :todos="todos" :total="totalTodo" @doneToDo="doneTodo" @deleteToDo="deleteTodo"></list>

		<div
			:class="totalTodo == 0 ? 'd-flex justify-content-between align-items-center my-3' : 'd-flex justify-content-between align-items-center'">
			<small>Total ToDo : {{ totalTodo }}</small>
			<button type="button" class="btn btn-sm btn-danger" v-if="totalTodo" @click="destroyToDo">
				<i class="bi bi-trash"></i>
			</button>
		</div>
	</div>
</template>

<script>
import List from './components/List.vue';

export default {
	data() {
		return {
			todo: '',
			todos: [],
		}
	},
	mounted() {
		this.todos = JSON.parse(localStorage.getItem('todos'))
	},
	components: { List },
	methods: {
		addTodo() {
			this.todos.unshift({
				activity: this.todo,
				isDone: false,
			})

			this.todo = ''

			this.saveLocalStorage()
		},
		doneTodo(indexTodo) {
			this.todos[indexTodo].isDone = !this.todos[indexTodo].isDone

			this.saveLocalStorage()
		},
		deleteTodo(indexTodo) {
			this.todos = this.todos.filter((item, index) => {
				if (index != indexTodo) {
					return true
				}
			})

			this.saveLocalStorage()
		},
		destroyToDo() {
			this.todos = []

			this.saveLocalStorage()
		},
		saveLocalStorage() {
			localStorage.setItem('todos', JSON.stringify(this.todos))
		}
	},
	computed: {
		totalTodo() {
			return this.todos.length
		}
	},
}
</script>

<style>
body {
	display: flex;
	min-height: 100vh;
	justify-content: center;
	align-items: center;
}
</style>
