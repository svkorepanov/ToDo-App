<template>
	<div class="add-task__overlay">
		<div class="add-task">
			<header class="add-task__header">
				<p class="add-task__action">Add New Task</p>
			</header>
			<form>
				<input class="add-task__input" type="text" name="task-name" id="">
				<button class="add-task__submit" type="submit">Ok</button>
			</form>
		</div>
	</div>
</template>

<script>
export default {
	
}
</script>

<style lang="scss">
	.add-task__header {
		margin-bottom: 60px;
	}

	.add-task {
		position: fixed;
		width: 420px;
		padding: 50px;
		padding-bottom: 40px;
		top: 50%;
		left: 50%;
		margin-left: -210px;
		background-color: #fff;
		z-index: 11;
	}

	.add-task__overlay {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: rgba(80, 227, 163, 0.8);
		z-index: 10;
	}

	.add-task__input {
		border: none;
		display: block;
		border-bottom: 3px solid #eef0f5;
		width: 100%;
		margin-bottom: 30px;
		font-family: inherit;
		font-size: inherit;

		&:focus {
			border-bottom-color: rgba(80, 227, 163, 0.8);
			outline: none;
		}
	}

	.add-task__submit {
		background-color: #50e3a4;
		border: none;
		border-radius: 20px;
		width: 170px;
		height: 40px;
		text-transform: uppercase;
		color: #fff;
		font: inherit;
		cursor: pointer;

		&:hover {
			
		}
	}
</style>

