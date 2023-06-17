<template>
  <button :style="css"> {{text}} </button>
</template>

<script>
export default {
  
	props:["x", "y", "width", "height", "text", "fontSize", "styl", "borderRadius"],
  
	data(){
		return{
			textColor : "",
			backgroundColor : "",
			borderColor: "",
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
				"--backgroundColor" : this.backgroundColor,
				"--borderColor" : this.borderColor,
				"--borderRadius" : this.borderRadius,
			}
		}
	},

	mounted() {
		if(this.styl == "normal"){
			this.textColor="white";
			this.backgroundColor="#0377fc";
			this.borderColor="transparent";
		}
		if(this.styl == "success"){
			this.textColor="white";
			this.backgroundColor="#04AA6D";
			this.borderColor="transparent";
		}
		if(this.styl == "danger"){
			this.textColor="white";
			this.backgroundColor="#9613cf";
			this.borderColor="transparent";
		}
		if(this.styl=="alternate"){
			this.textColor="white";
			this.backgroundColor="#cf1313";
			this.borderColor="transparent";
		}
		if(this.styl=="secondary"){
			this.textColor="#858585";
			this.backgroundColor="transparent";
			this.borderColor="#d6d6d6";
		}
	},
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans:wght@400;500&display=swap');
button{
  left:var(--x);
  top:var(--y);
  width:var(--width);
  height:var(--height);
  color:var(--textColor);
  background-color:var(--backgroundColor);
  border:0.15em solid var(--borderColor);
  font-size:var(--fontSize);
  border-radius:var(--borderRadius);

  position:absolute;
  outline:none;
  text-decoration:none;
  font-family: 'Noto Sans', sans-serif;
  font-weight:500;
  transition:0.1s all;
  display:flex;
  justify-content:center;
  align-items:center;
  cursor:pointer;
}
button:hover{
  filter:brightness(90%);
}
</style>
