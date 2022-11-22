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

		<list :todos="list" :total="totalTodo" @doneToDo="doneTodo" @deleteToDo="deleteTodo"></list>

		<div
			:class="totalTodo == 0 ? 'd-flex justify-content-between align-items-center my-3' : 'd-flex justify-content-between align-items-center'">
			<small>Total ToDo : {{ totalTodo }}</small>
			<button type="button" class="btn btn-sm btn-danger" v-if="totalTodo" @click="destroyTodo">
				<i class="bi bi-trash"></i>
			</button>
		</div>
	</div>
</template>

<script>
import { computed, onBeforeMount, onMounted, reactive, ref, toRefs } from 'vue';
import List from './components/List.vue';

export default {
	components: { List },
	setup() {
		const todo = ref('')
		const todos = reactive({
			list: []
		})

		onBeforeMount(() => {
			if (JSON.parse(localStorage.getItem('todos'))) {
				return true
			}

			saveLocalStorage()
		})
		
		onMounted(() => {
			todos.list = JSON.parse(localStorage.getItem('todos'))
		})

		const addTodo = () => {
			todos.list.unshift({
				activity: todo.value,
				isDone: false,
			})

			todo.value = ''

			saveLocalStorage()
		}

		const doneTodo = (indexTodo) => {
			todos.list[indexTodo].isDone = !todos.list[indexTodo].isDone

			saveLocalStorage()
		}

		const deleteTodo = (indexTodo) => {
			todos.list = todos.list.filter((item, index) => {
				if (index != indexTodo) {
					return true
				}
			})

			saveLocalStorage()
		}

		const destroyTodo = () => {
			todos.list = []

			saveLocalStorage()
		}

		const saveLocalStorage = () => {
			localStorage.setItem('todos', JSON.stringify(todos.list))
		}

		const totalTodo = computed(() => {
			return todos.list.length
		})

		return { todo, ...toRefs(todos), addTodo, doneTodo, deleteTodo, destroyTodo, totalTodo }
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
