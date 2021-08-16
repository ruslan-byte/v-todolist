<template>
	<div class="app">
		<vToDo/>
	</div>
</template>

<script>
import vToDo from "@/components/v-Todo"
export default {
	name: 'App',
	components:{vToDo,}
}
</script>
<style lang="scss">
	.app .v-todo{ margin:0 auto; }
</style>
