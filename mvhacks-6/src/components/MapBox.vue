<template>
	<div :style="css">{{text}}</div>
</template>

<script>

export default{
	props:["x", "y", "width", "height", "text", "fontSize", "color", "on"],
	data(){
		return{
			textColor:"",
			backgroundColor:"",
		}
	},
	computed: {
		css(){
			return{
				"--x" : this.x,
				"--y" : this.y,
				"--width" : this.width,
				"--height" : this.height,
				"--fontSize" : this.fontSize,
				"--textColor" : this.textColor,
				"--backgroundColor" : this.backgroundColor
			}
		}
	},
	
	mounted(){
		if(this.on=='true'){
			this.textColor="white";
			this.backgroundColor=this.color;
		}else{
			this.textColor="black";
			this.backgroundColor="transparent";
		}
	}
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;500;600&display=swap');
div{
	position:absolute;
	left:calc(var(--x) - var(--width) / 2 + 3px);
	top:calc(var(--y) - var(--height) / 2 );
	width:var(--width);
	height:var(--height);
	background-color:var(--backgroundColor);
	color:var(--textColor);
	font-size:var(--fontSize);
	display:flex;
	justify-content:center;
	align-items:center;
	font-family: 'Open Sans', sans-serif;
}
</style>