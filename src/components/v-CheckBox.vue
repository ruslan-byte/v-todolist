<template>
	<div class="check-box">
		<input type="checkbox" :id="key" :checked="checkBoxData.checked">
		<div class="check-box__marker" @click="click">
			<svg width="11" height="9" viewBox="0 0 11 9" fill="none" xmlns="http://www.w3.org/2000/svg">
				<path d="M0.126923 4.92308C0.0423077 4.83847 0 4.71154 0 4.62693C0 4.54231 0.0423077 4.41539 0.126923 4.33077L0.719231 3.73847C0.888462 3.56924 1.14231 3.56924 1.31154 3.73847L1.35385 3.78077L3.68077 6.27693C3.76538 6.36154 3.89231 6.36154 3.97692 6.27693L9.64615 0.396159H9.68846C9.85769 0.226928 10.1115 0.226928 10.2808 0.396159L10.8731 0.988467C11.0423 1.1577 11.0423 1.41154 10.8731 1.58077L4.10385 8.60385C4.01923 8.68847 3.93462 8.73077 3.80769 8.73077C3.68077 8.73077 3.59615 8.68847 3.51154 8.60385L0.211538 5.05001L0.126923 4.92308Z" fill="white"/>
			</svg>
		</div>
		<div class="check-box__text" @click="openCorrectTestPopup" >
			{{checkBoxData.text}}
		</div>
		<CorrectTaskPopup
			:visibility="correctTextPopupVisibility"
			@closePopup="correctTextPopupVisibility = false"
			:taskText="checkBoxData.text"
			@saveNewTaskText="$emit('changeTaskText')"
			:checkBoxData="checkBoxData"
		/>
	</div>
</template>
<script>
	//TODO переделать все в composition API
	import CorrectTaskPopup from "@/components/CorrectTaskPopup"
	export default
	{
		name: "v-check-box",
		props: {
			checkBoxData: {
				type: Object,
				required: true
			},
			key: Number,
		},
		data(){
			return{
				correctTextPopupVisibility:true,
			}
		},
		methods:{
			click() {
				console.log(123)
				this.$emit('check');
			},
			openCorrectTestPopup(){
				this.correctTextPopupVisibility=true;
			},
			changeTaskText(newtext,index){
				this.$emit('changeTaskText',newtext, index);
			}
		},
		components:{
			CorrectTaskPopup,
		}
	}
</script>

<style lang="scss">
	.check-box
	{
		display: flex;
		align-items: center;
		white-space: nowrap;
		position: relative;
		color: #4F4F4F;
		input[type="checkbox"]
		{
			position: absolute;
			width: 0px;
			height: 0px;
		}
		.check-box__marker
		{
			position: relative;
			border: 1px solid #E0E0E0;
			border-radius: 3px;
			width: 24px;
			height: 24px;
			background: #F2F2F2;
			border-radius: 3px;
			margin-right: 12px;
			cursor: pointer;
			svg
			{
				display: none;
				position: absolute;
				top:28%;
				left:28%;
			}
		}
		input:checked + .check-box__marker
		{
			background: #6FCF97;
			box-shadow: inset 0 0 0 1px #27AE60;
			border-radius: 3px;
			svg{ display: block;}
		}
		.check-box__text
		{
			white-space: normal;
			max-width: 434px;
			height: 30px;
			width: 100%;
			user-select: none;
			cursor: pointer;
			position: relative;
			textarea
			{
				// display: none;
				width: 100%;
				position: absolute;
				top:0;
				left:0;
				background:transparent;
				border:none;
			}
			textarea:focus-visible
			{
				border:none;
			}
		}
		input:checked ~ .check-box__text
		{
			transition: all 0.33s;
			text-decoration: line-through;
			color:#BDBDBD;
		}

	}
</style>
