<template>
	<div class="app">
		<vToDo/>
	</div>
</template>

<script>
import vToDo from "@/components/Todo"
export default {
	name: 'App',
	components:{vToDo,}
}
</script>
<style lang="scss">
	.app .v-todo{ margin:0 auto; }
	.app
	{
		background: #f3f3f3;
		width: 100vw;
		min-height: 100vh;
		padding-top: 60px;
		padding-bottom: 60px;
	}
	body{ margin: 0;}
</style>
