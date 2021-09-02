<template>
	<div class="v-todo-list">
		<div class="v-todo-list__date">
			{{listTaskForDayData.date}}
		</div>
		<checkBox
			class="v-todo-list__item"
			v-for="checkBoxItemData of listTaskForDayData.checkBoxes"
			:key="checkBoxItemData.index"
			:checkBoxData="checkBoxItemData"
			@check="checkBoxItemData.isChecked = !checkBoxItemData.isChecked"
			@changeTaskText="changeTaskText"
			@clickOnText="clickOnText"
		>
		</checkBox>
	</div>
</template>
<script>
	import checkBox from "@/components/CheckBox"
	export default{
		name:"v-todo-list",
		components:{checkBox},
		props: {
			listTaskForDayData:Object,
		},
		setup(props, {emit} ){
			function changeTaskText(newText, checkBoxIndex) {
				emit('changeTaskText', newText, checkBoxIndex);
			}
			function clickOnText(checkBoxIndex) {
				emit('clickOnText', checkBoxIndex);
			}
			return {changeTaskText, clickOnText}
		}
	}
</script>
<style lang="scss">
	.v-todo-list__date
	{
		margin-bottom: 16px;
		color:#333333;
	}
	.v-todo-list__item{ margin-bottom: 27px;}
</style>