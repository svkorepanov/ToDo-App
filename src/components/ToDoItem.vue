<template>
	<li class="todo-list__item"
		:class="{'todo-list__item--checked' : this.todo.completed}"
	>
		<span class="todo-list__item-title">{{ todo.title | capitalize }}</span>
		<button type="button" class="todo-list__check"
			@click="onCheckClick"
			:class="{'todo-list__check--checked': this.todo.completed}"
		></button>
	</li>
</template>

<script>
export default {
	props: {
		todo : {
			type: Object,
			required: true
		}
	},
	methods: {
		onCheckClick() {
			this.todo.completed = !this.todo.completed;
		}
	},
	filters: {
  capitalize: function (value) {
    if (!value) return ''
    value = value.toString()
    return value.charAt(0).toUpperCase() + value.slice(1)
  }
}
}
</script>

<style lang="scss">
	.todo-list__item {
		display: flex;
		justify-content: space-between;
		align-items: center;

		&:not(:last-child) {
			margin-bottom: 30px;
		}

		&--checked {
			color: #bdc0ca;
		}
	}

	.todo-list__item-title {
		padding-right: 10px;
	}

	.todo-list__check {
		width: 30px;
		height: 30px;
		border: 4px solid #eef0f5;
		border-radius: 50%;
		background-color: transparent;
		flex-shrink: 0;
		cursor: pointer;
		outline: none;
		transition: transform 0.1s ease-out;

		&:hover {
			transform: scale(1.2);
			border-color: transparentize($color: #50e3a4, $amount: 0.5);
		}

		&--checked {
			border-color: #50e3a4;
			background-image: url('../assets/checked.png');
			background-repeat: no-repeat;
			background-position: 50% 50%;
			background-size: 80%;
		}
	}
</style>
