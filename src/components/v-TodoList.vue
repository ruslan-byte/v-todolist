<template>
	<div class="v-todo-list">
		<checkBox
			v-for="checkBoxItemData of data.checkBoxes"
			:key="checkBoxItemData.index"
			:checkBoxData="checkBoxItemData"
			@check="checkBoxItemData.isChecked = !checkBoxItemData.isChecked"
			@changeTaskText="changeTaskText"
		>
		</checkBox>
	</div>
</template>
<script>
	//TODO сделать нормальный выход из попапа по нажатию esc
	//TODO настроить scss переменные
	//TODO Сделать emmit тут и передать данные по-нормальному
	import checkBox from "@/components/v-CheckBox"
	export default{
		name:"v-todo-list",
		components:{checkBox},
		props:{
			data:Object,
		},
		setup(props, {emit} ){
			function changeTaskText(newText, checkBoxIndex) {
				// let checkBox = props.data.checkBoxes.find((item)=>item.index === checkBoxIndex);
				// checkBox.taskText = newText;
				// console.log(checkBox)
				emit('changeTaskText', newtext, checkBoxIndex);
			}
			return {changeTaskText}
		}
	}
</script>
<style lang="scss">
</style>