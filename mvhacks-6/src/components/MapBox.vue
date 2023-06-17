<template>
	<div v-if="on=='true'" :style="css"></div>
</template>

<script>

export default{
	props:["x", "y", "width", "height", "text", "fontSize", "color", "on"],
	computed: {
		css(){
			return{
				"--x" : this.x,
				"--y" : this.y,
				"--width" : this.width,
				"--height" : this.height,
				"--fontSize" : this.fontSize,
				"--color" : this.color,
				
			}
		}
	},
}
</script>

<style scoped>
div{
	position:absolute;
	left:var(--x);
	top:var(--y);
	width:var(--width);
	height:var(--height);
	background-color:var(--color);
	color:white;
	font-size:var(--fontSize);
	display:flex;
	justify-content:center;
	align-items:center;
}
</style>