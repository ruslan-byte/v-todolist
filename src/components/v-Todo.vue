<template>
	<div class="v-todo">
		<vToDoList
			v-for="(item, index) of TodoData"
			:key="index"
			:data="item"
			@changeTaskText="changeTaskText"
		/>
	</div>
</template>
<script>

	import vToDoList from "@/components/v-TodoList"
	import { ref } from "vue"
	export default{
		name:"v-todo",
		components:{vToDoList},
		setup(){
			let TodoData = ref([
				{
					date:'20 января',
					checkBoxes: [
						{index:1,taskText: 'Lorem nostrud eiusmod id duis est commodo elit velit Lorem aute laborum consequat exercitation aute.', isChecked: false,},
						{index:2,taskText: 'Eiusmod minim incididunt voluptate pariatur consectetur eu est culpa ipsum eiusmod ut aute reprehenderit.', isChecked: false,},
						{index:3,taskText: 'Velit amet et est tempor id nostrud dolor exercitation ut sint sit sunt aliquip Lorem.', isChecked: false,},
						{index:4,taskText: 'Incididunt adipisicing aliquip et incididunt tempor duis anim cupidatat eu do velit nisi magna.', isChecked: false,},
					]
				},
				{
					date:'21 января',
					checkBoxes: [
						{index:5,taskText: 'Lorem nostrud eiusmod id duis est commodo elit velit Lorem aute laborum consequat exercitation aute.', isChecked: false,},
						{index:6,taskText: 'Eiusmod minim incididunt voluptate pariatur consectetur eu est culpa ipsum eiusmod ut aute reprehenderit.', isChecked: false,},
						{index:7,taskText: 'Velit amet et est tempor id nostrud dolor exercitation ut sint sit sunt aliquip Lorem.', isChecked: false,},
						{index:8,taskText: 'Incididunt adipisicing aliquip et incididunt tempor duis anim cupidatat eu do velit nisi magna.', isChecked: false,},
					]
				},
			])
			function changeTaskText(newtext, checkBoxIndex) {

				// let checkBox =
				// 	this.TodoData.find(
				// 		(item)=>{item.checkBoxes === checkBoxIndex});

				// checkBox.taskText = newText;
			}
			return {TodoData,changeTaskText}
		}
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