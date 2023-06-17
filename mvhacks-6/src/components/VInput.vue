<template>	
	<input type="text" v-model="in" :style="css"/>
	<div :style="css"> {{label}} </div>
</template>

<script>
export default{
	
	props:["x", "y", "width", "height", "label", "fontSize"],
	
	data(){
		return{
			in : "",
		}
	},
	
	computed:{
		css(){
			return{
				"--x" : this.x,
				"--y" : this.y,
				"--width" : this.width,
				"--height" : this.height,
				"--fontSize" : this.fontSize,
			}
		}
	},
	
	watch:{
		in(newIn){
			localStorage.setItem(this.label,newIn);
		},
	},
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans:wght@400;500&display=swap');
input{
	left:var(--x);
	top:var(--y);
	width:var(--width);
	height:var(--height);
	font-size:var(--fontSize);
	
	position:absolute;
	border-radius:5px;
	font-family: 'Noto Sans', sans-serif;
	font-weight:500;
	border:2px solid rgba(0,0,0,0);
	background-color:rgba(100,100,100,0.12);
	transition:0.1s all;
	padding-left:20px;
}
input:hover{
	background-color:rgba(100,100,100,0.2);
}
input:focus{
	outline:none;
	border:2px solid #0377fc;
	background-color:rgba(100,100,100,0.12);
}
input:focus + div{
	color:#0377fc;
}
div{
	left:var(--x);
	top:calc(var(--y) - 35px);
	
	position:absolute;
	font-size:calc(var(--fontSize) / 1.2);
	font-family: 'Noto Sans', sans-serif;
	font-weight:500;
	color:rgba(100,100,100,0.8);
}
</style>