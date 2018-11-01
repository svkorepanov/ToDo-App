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
			<button class="add-task__close" type="button"
				@click="$emit('closeModal')"
			>
				<IconClose
					width="40"
					height="40"
					class="add-task__close-img"
				/>
			</button>
		</div>
	</div>
</template>

<script>
import IconClose from "./icons/IconClose.vue";

export default {
	components: {
		IconClose
	}
}
</script>

<style lang="scss">
	.add-task__header {
		margin-bottom: 60px;
	}

	.add-task {
		position: relative;
		margin: auto;
		width: 420px;
		padding: 50px;
		padding-bottom: 40px;
		background-color: #fff;
		z-index: 11;
	}

	.add-task__close {
		position: absolute;
		top: 20px;
		right: 20px;
		border: none;
		background: transparent;
		outline: none;
		cursor: pointer;
		transform-origin: 50% 50%;

		&:hover {

			.add-task__close-img {
				transform: rotate(180deg);
				fill: #000;
			}
		}
		

		&:active .add-task__close-img{
			fill: transparentize($color: #000000, $amount: 0.6)
		}
	}

	.add-task__close-img {
		fill: #eef0f5;
		transition: 
			transform 0.4s ease-out,
			fill 0.1s ease-in;
	}

	.add-task__overlay {
		display: flex;
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
		padding: 0 5px;
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
		transition: all 0.1s ease-out;
		outline: none;

		&:hover {
			transform: translateY(-3px);
			box-shadow: 0 6px 10px 0 rgba(62, 192, 136, 0.8);
		}

		&:active {
			box-shadow: 0 3px 10px 0 rgba(62, 192, 136, 0.8);
		}
	}
</style>

