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
	import { ref, watch } from "vue"
	export default {
		props: {
			active:String
		},
		setup() {
			const Main = ref(null);
			watch(Main, ()=>{
				if(Main.value != null) Main.value.focus();
			});
			return{Main}
		}
	}
</script>
<style lang="scss">
.add-task-animation-enter-active, .add-task-animation-leave-active {
	transition: all .5s;
}
.add-task-animation-enter, .add-task-animation-leave-to {
	height: 0;
}
.add-task textarea
{
	transition: all .5s;
	width: 100%;
	border-radius: 4px;
	height: 150px;
	resize: none;
	overflow: auto;
	margin-bottom: 10px;
}
</style>