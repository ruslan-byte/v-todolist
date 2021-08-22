<template>
	<div class="v-todo-list">
		<checkBox
			v-for="checkBoxItemData of data.checkBoxes"
			:key="checkBoxItemData.index"
			:checkBoxData="checkBoxItemData"
			@check="checkBoxItemData.isChecked = !checkBoxItemData.isChecked"
			@changeTaskText="changeTaskText"
			@clickOnText="openPopup"
		>
		</checkBox>
		<CorrectTaskPopup
			:visibility="isPopupVisibility"
			@closePopup="isPopupVisibility = false"
			:taskText="popupCheckBoxText"
			@saveNewTaskText="changeTaskText"
			:checkBoxData="checkBoxData"
		/>
	</div>
</template>
<script>
	//TODO сделать нормальный выход из попапа по нажатию esc
	//TODO настроить scss переменные
	import checkBox from "@/components/v-CheckBox"
	import CorrectTaskPopup from "@/components/CorrectTaskPopup"
	import { ref } from 'vue'
	export default{
		name:"v-todo-list",
		components:{checkBox, CorrectTaskPopup},
		props:{
			data:Object,
		},
		setup(props, {emit} ){
			let isPopupVisibility = ref(false),
			popupCheckBoxText = ref(''),
			popupCheckBoxIndex = ref('');
			function changeTaskText(newText, checkBoxIndex) {
				emit('changeTaskText', newText, checkBoxIndex);
			}
			function openPopup(checkBoxIndex){
				popupCheckBoxIndex.value = checkBoxIndex;
				console.log(checkBoxIndex)
				popupCheckBoxText.value = props.data.checkBoxes.find((checkBox)=>{checkBox.index == checkBoxIndex}).taskText;
				isPopupVisibility.value = true;
				console.log(popupCheckBoxText)
			}
			return {changeTaskText, openPopup, popupCheckBoxText}
		}
	}
</script>
<style lang="scss">
</style>