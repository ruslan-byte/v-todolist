<template>
	<div class="v-todo-list">
		<checkBox
			v-for="checkBoxItemData of checkBoxes"
			:key="checkBoxItemData.index"
			:checkBoxData="checkBoxItemData"
			@check="checkBoxItemData.checked = !checkBoxItemData.checked"
			:checkId="checkBoxItemData.index"
			@changeTaskText="changeTaskText"
		>
		</checkBox>
	</div>
</template>
<script>
	import checkBox from "@/components/v-CheckBox"
	export default{
		name:"v-todo-list",

		components:{checkBox},

		data(){
			return {
				checkBoxes: [
					{index:1,text: 'Lorem nostrud eiusmod id duis est commodo elit velit Lorem aute laborum consequat exercitation aute.', checked: false,},
					// {index:2,text: 'Eiusmod minim incididunt voluptate pariatur consectetur eu est culpa ipsum eiusmod ut aute reprehenderit.', checked: false,},
					// {index:3,text: 'Velit amet et est tempor id nostrud dolor exercitation ut sint sit sunt aliquip Lorem.', checked: false,},
					// {index:4,text: 'Incididunt adipisicing aliquip et incididunt tempor duis anim cupidatat eu do velit nisi magna.', checked: false,},
				]
			}
		},
		methods: {
			changeTaskText(newText, checkBoxIndex) {
				this.checkBoxes[checkBoxIndex].text = newText;
				console.log(123)

			}
		}
	}
</script>
<style lang="scss">
</style>