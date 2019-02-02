<template>
	<div>
		<ul
			v-if="todos.length"
			class="todo-list"
		>
			<ToDoItem 
				v-for="todo in todos" 
				:key="todo.id"
				:todo="todo"
			/>
		</ul>
		<a href="#" class="todo-list__add-item"
			@click.prevent="isNewTask = true"
		>+</a>
		<transition name="new-task">
			<NewTask 
				v-if="isNewTask"
				@closeModal="isNewTask = false"
				@addNewTask="onAddNewTask"
			/>
		</transition>
	</div>
</template>

<script>
import ToDoItem from './ToDoItem.vue';
import NewTask from "./NewTask";

export default {
	components: {
		ToDoItem,
		NewTask
	},
	data() {
		return {
			todos: [],
			GET_URL: 'https://jsonplaceholder.typicode.com/users/1/todos',
			POST_URL: 'https://jsonplaceholder.typicode.com/todos',
			isNewTask: false
		}
	},
	methods: {
		onAddNewTask(newTaskTitle) {
			const newObj = {
				userID: 1,
				id: this.todos[this.todos.length - 1].id + 1,
				title: newTaskTitle,
				completed: false
			};
			const task = new FormData();
			Object.entries(newObj).forEach((item) => {
        task.append(...item);
			});
			fetch(this.POST_URL, {
				method: 'POST',
				body: task
			})
				.then(() => {
					this.addTask(newObj);
					this.isNewTask = false;
				})
				.catch(() => {
					
				})
		},
		addTask(task) {
			this.todos.push(task);
		}
	},
  created : function () {
    const vm = this;
    fetch(this.GET_URL)
      .then((response) => response.json())
      .then((json) => vm.todos.push(...json))
      // .catch(error => console.log(error))
  }
}
</script>

<style lang="scss">
// vue transition
	.new-task {
		&-enter-active,
		&-leave-active {
			transition: opacity 0.4s ease-in-out;
		}

		&-enter,
		&-leave-to {
			opacity: 0;
		}
	}

	.todo-list {
		&-enter-active,
		&-leave-active {
			transition: all 1.3s ease-in-out;
		}

		&-enter,
		&-leave-to {
			opacity: 0;
			transform: translateX(-100px);
		}
	}

// vue transition end
	.todo-list {
		margin: 0;
		padding: 0;
		margin-bottom: 50px;
		list-style: none;
		text-align: left;
	}

	.todo-list__add-item {
		position: absolute;
		width: 90px;
		height: 90px;
		left: 50%;
		top: 100%;
		margin-left: -45px;
		margin-top: -45px;
		border-radius: 50%;
		background-color: #50e3a4;
		box-shadow: 0 3px 10px 0 rgba(62, 192, 136, 0.8);
		color: #46be8b;
		font-size: 55px;
		text-decoration: none;
		line-height: 90px;
		transition: all 0.1s ease-out;

		&:hover {
			transform: translateY(-3px);
			box-shadow: 0 6px 10px 0 rgba(62, 192, 136, 0.8);
		}

		&:active {
			box-shadow: 0 3px 10px 0 rgba(62, 192, 136, 0.8);
		}
	}
</style>
