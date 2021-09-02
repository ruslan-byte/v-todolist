<template>
	<div class="v-todo">
		<vToDoList
			v-for="(item, index) of todoData"
			:key="index"
			:listTaskForDayData="item"
			@changeTaskText="changeTaskText"
			@clickOnText="openPopup"
		/>
		<component :is="vButton" ></component>

		<addTaskPlace :active="isAddTaskPlaceVisibility" />

		<vButton @click="isAddTaskPlaceVisibility = !isAddTaskPlaceVisibility" >Добавить задачу</vButton>
		<CorrectTaskPopup
			:visibility="isPopupVisibility"
			@closePopup="isPopupVisibility = false"
			:popupCheckBox="popupCheckBox"
			@saveNewTaskText="changeTaskText"
		/>
	</div>
</template>
<script>
	import vToDoList from "@/components/TodoList"
	import CorrectTaskPopup from "@/components/CorrectTaskPopup"
	import addTaskPlace from "@/components/addTaskPlace"
	import vButton from "@/components/Button"
	import { ref } from "vue"
	export default {
		name:"v-todo",
		components:{vToDoList, CorrectTaskPopup, vButton, addTaskPlace},
		setup(){
			let isPopupVisibility = ref(false),
				isAddTaskPlaceVisibility = ref(false),
				popupCheckBox = ref(''),
				todoData = ref([
					{
						date:'На Сегодня 20 января 2020г',
						checkBoxes: [
							{index:1,taskText: 'Lorem nostrud eiusmod id duis est commodo elit velit Lorem aute laborum consequat exercitation aute.', isChecked: false,},
							{index:2,taskText: 'Eiusmod minim incididunt voluptate pariatur consectetur eu est culpa ipsum eiusmod ut aute reprehenderit.', isChecked: false,},
							{index:3,taskText: 'Velit amet et est tempor id nostrud dolor exercitation ut sint sit sunt aliquip Lorem.', isChecked: false,},
							{index:4,taskText: 'Incididunt adipisicing aliquip et incididunt tempor duis anim cupidatat eu do velit nisi magna.', isChecked: false,},
						]
					},
					{
						date:'На Завтра 21 января 2020г',
						checkBoxes: [
							{index:5,taskText: 'Lorem nostrud eiusmod id duis est commodo elit velit Lorem aute laborum consequat exercitation aute.', isChecked: false,},
							{index:6,taskText: 'Eiusmod minim incididunt voluptate pariatur consectetur eu est culpa ipsum eiusmod ut aute reprehenderit.', isChecked: false,},
							{index:7,taskText: 'Velit amet et est tempor id nostrud dolor exercitation ut sint sit sunt aliquip Lorem.', isChecked: false,},
						]
					},
				]);
			function openPopup(checkBoxIndex){
				/*
				** Ищем чекбокс, которому соответствует полученный индекс и сохраняем его в переменную
				*/
				todoData.value.forEach((todoList)=>{ popupCheckBox.value = (todoList.checkBoxes.find((checkBox)=>checkBox.index == checkBoxIndex)) ? todoList.checkBoxes.find((checkBox)=>checkBox.index == checkBoxIndex ) : popupCheckBox.value});
				isPopupVisibility.value = true;
			}
			function changeTaskText(newtext) {
				popupCheckBox.value.taskText = newtext;
			}
			return {todoData, changeTaskText, isPopupVisibility, openPopup, popupCheckBox, isAddTaskPlaceVisibility}
		}
	}
</script>
<style lang="scss">
	.v-todo
	{
		padding: 20px;
		width: 100vw;
		max-width: 474px;
		border-radius: 4px;
		background: #fff;
	}
</style>