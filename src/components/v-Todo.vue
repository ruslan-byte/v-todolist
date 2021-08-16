<template>
	<div class="v-todo">
		<vToDoList/>
	</div>
</template>
<script>
	import vToDoList from "@/components/v-TodoList"
	export default{
		name:"v-todo",
		components:{vToDoList},
	}
</script>
<style lang="scss">
	.v-todo
	{
		width: 100vw;
		height: 100vh;
		max-width: 514px;
		max-height: 523px;
		border:1px solid gray;
		border-radius: 4px;
	}
</style>