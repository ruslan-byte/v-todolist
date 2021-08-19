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
<style>
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
}
</style>