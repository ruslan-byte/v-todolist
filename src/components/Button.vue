<template>
	<button class="v-button">
		<slot></slot>
	</button>
</template>
<script>
	export default {
		name:"vue-button",
	}
</script>
<style lang="scss">
	.v-button
	{
		display: block;
		width: 100%;
		background: #27AE60;
		height: 48px;
		border:none;
		border-radius: 4px;
		cursor:pointer;
		color:#ffffff;
		font-size: 16px;
		line-height: 19px;
		text-align: center;
		.sub
		{
			display: none;
			font-size: 12px;
			line-height: 12px;
		}
	}
	.v-button:hover .sub{ display: inline }
</style>