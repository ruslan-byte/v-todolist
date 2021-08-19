<template>
	<div class="correct-tast-popup" v-if="visibility" >
		<div class="correct-tast-popup__background" @click="closePopup"></div>
		<div class="correct-tast-popup__body">
			<textarea v-model="newTaskText"></textarea>
			<vueButton @click="saveNewTaskText">Сохранить</vueButton>
		</div>
	</div>
</template>
<script>
	import vueButton from "@/components/Button"
	import { ref } from 'vue'
	export default {
		name:"correct-task-popup",
		props: {
			visibility:Boolean,
			taskText:String,
			checkBoxData:Object,
		},
		setup(props){
			let newTaskText = ref(props.taskText);
			return{newTaskText}
		},
		methods:{
			closePopup(){
				this.$emit('closePopup');
			},
			saveNewTaskText(){
				this.$emit('saveNewTaskText', this.newTaskText, this.checkBoxData.index)
			},
		},
		components:{
			vueButton,
		}
	}
</script>
<style lang="scss">
	.correct-tast-popup
	{
		width: 100vw;
		height: 100vh;
		position: fixed;
		left:0;
		top:0;
	}
	.correct-tast-popup__background
	{
		background: rgba(0,0,0,.4);
		width: 100vw;
		height: 100vh;
		position: fixed;
		z-index: -1;
	}
	.correct-tast-popup__body
	{
		width: 100vw;
		max-width: 514px;
		max-height: 523px;
		border-radius: 4px;
		background:#ffffff;
		margin-inline: auto;
		margin-top: 30vh;
		padding: 10px;
		textarea
		{
			width: 508px;
			border-radius: 4px;
			height: 150px;
			resize: none;
			overflow: auto;
			margin-bottom: 10px;
		}
	}
</style>