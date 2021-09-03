<template>
	<transition name="add-task-animation">
		<div class="add-task" v-if="active">
			<textarea
				v-model="newTaskText"
				placeholder="Новая задача"
			/>
		</div>
	</transition>
</template>
<script>
	export default {
		props: {
			active:Boolean
		},
	}
</script>
<style lang="scss">
.add-task textarea
{
	display: block;
	max-height: 150px;
	width: 457px;
	height: 150px;
	padding: 10px 0 0 15px;
	border-radius: 4px;
	resize: none;
	overflow: auto;
	margin-bottom: 10px;
	opacity: 1;
}
.add-task{ transition: max-height 0.5s;}
.add-task-animation-enter-active textarea,
.add-task-animation-leave-active textarea {
	transition: all 0.5s;
}
.add-task-animation-enter-from textarea,
.add-task-animation-leave-to textarea{
	max-height: 0;
	opacity: 0
}
</style>