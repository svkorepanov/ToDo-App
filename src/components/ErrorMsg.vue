<template>
	<p class="error-msg">
		{{ msg }}
	</p>
</template>

<script>
export default {
	props: {
		msg: {
			type: String,
			required: true
		}
	}
}
</script>

<style lang="scss">
	.error-msg {
		margin: 0;
		padding: 20px;
		position: fixed;
		top: 30px;
		right: 30px;
		background-color: #fff;
		box-shadow: 0px 3px 15px 0px rgba(0, 0, 0, 0.3);
	}
</style>
