<template>
	<transition name="correct-task-popup-animation">
		<div
			class="correct-task-popup"
			v-if="visibility"
			@keyup.esc="closePopup"
			@keyup.ctrl.enter="saveNewTaskTextAndClose"
			tabindex="0"
			ref="popupMain"
		>
			<div
				class="correct-task-popup__background"
				@click="closePopup"
			/>
			<div class="correct-task-popup__body">
				<textarea
					v-model="newTaskText"
					placeholder="Новая задача"
				/>
				<vueButton @click="saveNewTaskTextAndClose">
					Сохранить <br> <span class="sub">(ctrl + enter)</span>
				</vueButton>
			</div>
		</div>
	</transition>
</template>
<script>
	import vueButton from "@/components/Button"
	import { ref , watch } from 'vue'
	export default {
		name: "correct-task-popup",
		props: {
			visibility:Boolean,
			popupCheckBox:Object,
		},
		components:{
			vueButton,
		},
		setup(props,{ emit }) {

			let newTaskText = ref('');
			const popupMain = ref(null);

			watch(props, ()=>{
				newTaskText.value = props.popupCheckBox.taskText
			});

			/*
			** Устанавливаем фокус на попап, для грамотной работы событий нажатия на клавиши
			*/
			watch(popupMain, ()=>{
				if(popupMain.value != null) popupMain.value.focus();
			});

			function closePopup() {
				newTaskText.value = props.taskText;
				emit('closePopup');
			}

			function valideText(text) {
				let isNotEmpty = text != '';
				return isNotEmpty;
			}

			function saveNewTaskTextAndClose() {
				if(valideText(newTaskText.value))
				{
					emit('saveNewTaskText', newTaskText.value);
					emit('closePopup');
				}
				else
				{
					newTaskText.value = "Новая задача";
					saveNewTaskTextAndClose();
				}
			}
			return{newTaskText, closePopup, saveNewTaskTextAndClose, popupMain}
		},
	}
</script>
<style lang="scss">

	.correct-task-popup-animation-enter-active{
		transition: opacity .15s;
	}

	.correct-task-popup-animation-enter-from{
		opacity: 0;
	}
	.correct-task-popup
	{
		width: 100vw;
		height: 100vh;
		position: fixed;
		left:0;
		top:0;
		z-index: 2;
	}
	.correct-task-popup__background
	{
		background: rgba(0,0,0,.4);
		width: 100vw;
		height: 100vh;
		position: fixed;
	}
	.correct-task-popup__body
	{
		position: relative;
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