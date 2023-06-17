<template>
    <router-link to="/" id="Home">MVHS Logistic Map</router-link>
    <VButton x="80%" y="3%" width="120px" height="60px" text="About" fontSize="25px" styl="secondary" borderRadius="10px" @click = "goToAbout"></VButton>
    <VButton x="90%" y="3%" width="120px" height="60px" text="Map" fontSize="25px" styl="normal" borderRadius="10px"></VButton>
    <div id="HeaderSeparator"></div>
    <img id="Map" src="../assets/map2.png">
	<div id="BoxContainer">
		
		<MapBox v-for="mapbox in mapboxes" :x="mapbox.x" :y="mapbox.y" :width="mapbox.width" :height="mapbox.height" :text="mapbox.name" fontSize="10px" color="#c2ffd3" on="false"></MapBox>
	</div>
	<div id="RightSeparator"></div>
	<div id="ViewSelector">
		<div id="ViewLabel">Select View</div>
		<button id="ClubsView" @click="selectClubs" class="">Clubs</button>
		<button id="LunchView" @click="selectLunch" class="notSelected">Lunch</button>
		<button id="TeachersView" @click="selectTeachers" class="notSelected">Teachers</button>
		<button id="EventsView" @click="selectEvents" class="notSelected">Events</button>
	</div>
	<input v-on:keyup.enter="onEnter" />


	
  </template>
<script>
  import VButton from "./VButton.vue";
  import MapBox from "./MapBox.vue";
  import VInput from "./VInput.vue";
  export default {
      data(){
		return{
			view:"clubs",
			mapboxes:"",

		}
	  },
	  components:{
          VButton,
		  MapBox,
		  VInput,
      },
      methods:{
          goToAbout(){
              window.location.href = "/about";
          },
		  goToMap(){
            window.location.href = "/map";
			},
		selectClubs(){
			document.getElementById("ClubsView").style.backgroundColor="#c2ffd3";
			document.getElementById("LunchView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("TeachersView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("EventsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("ClubsView").classList.remove("notSelected");
			document.getElementById("LunchView").classList.add("notSelected");
			document.getElementById("TeachersView").classList.add("notSelected");
			document.getElementById("EventsView").classList.add("notSelected");
			this.view="clubs";
		},
		selectLunch(){
			document.getElementById("ClubsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("LunchView").style.backgroundColor="#c2ffd3";
			document.getElementById("TeachersView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("EventsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("ClubsView").classList.add("notSelected");
			document.getElementById("LunchView").classList.remove("notSelected");
			document.getElementById("TeachersView").classList.add("notSelected");
			document.getElementById("EventsView").classList.add("notSelected");
			this.view="lunch";
		},
		selectTeachers(){
			document.getElementById("ClubsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("LunchView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("TeachersView").style.backgroundColor="#c2ffd3";
			document.getElementById("EventsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("ClubsView").classList.add("notSelected");
			document.getElementById("LunchView").classList.add("notSelected");
			document.getElementById("TeachersView").classList.remove("notSelected");
			document.getElementById("EventsView").classList.add("notSelected");
			this.view="teachers";
		},
		selectEvents(){
			document.getElementById("ClubsView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("LunchView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("TeachersView").style.backgroundColor="rgba(100,100,100,0.05)";
			document.getElementById("EventsView").style.backgroundColor="#c2ffd3";
			document.getElementById("ClubsView").classList.add("notSelected");
			document.getElementById("LunchView").classList.add("notSelected");
			document.getElementById("TeachersView").classList.add("notSelected");
			document.getElementById("EventsView").classList.remove("notSelected");
			this.view="events";
		},
		onEnter(){
			console.log("enter");
		},
		
      },
      mounted(){
		
      },
  }
</script>
  
<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;500;600&display=swap');
  #Pitch{
      font-family: 'Open Sans', sans-serif;
      font-size:80px;
      font-weight:600;
      position:absolute;
      width:50%;
      height:10%;
      left:0%;
      top:25%;
      text-align:center;
  }
  #Pitch2{
      font-family: 'Open Sans', sans-serif;
      font-size:100px;
      font-weight:600;
      position:absolute;
      width:50%;
      height:15%;
      left:0%;
      top:35%;
      text-align:center;
  }
  #SubPitch{
      font-family: 'Open Sans', sans-serif;
      font-size:30px;
      font-weight:500;
      position:absolute;
      width:50%;
      height:10%;
      left:0%;
      top:55%;
      text-align:center;
  }
  .linear-wipe {
    background: linear-gradient(
          to right,
          #00db96 20%,
          #00affa 30%,
          #0190cd 70%,
          #00db66 80%
      );
      -webkit-background-clip: text;
      background-clip: text;
      -webkit-text-fill-color: transparent;
      text-fill-color: transparent;
      background-size: 500% auto;
      animation: textShine 3s ease-in-out infinite alternate;
  }
  @keyframes textShine {
      0% {
          background-position: 0% 50%;
      }
      100% {
          background-position: 100% 50%;
      }
  }
  #MapArt{
      width:40%;
      position:absolute;
      left:50%;
      top:20%;
      animation-name:float;
      animation-duration:3s;
      animation-iteration-count:infinite;
      animation-timing-function:ease;
  }
  @keyframes float{
      0% { transform: translate(0,  0px); }
      50%  { transform: translate(0px, 25px); }
      100%   { transform: translate(-0, -0px); }   
  }
  #Home{
      width:20%;
      position:absolute;
      left:0%;
      height:10%;
      top:0%;
      display:flex;
      align-items:center;
      text-align:left;
      text-decoration:none;
      padding-left:40px;
      padding-top:10px;
      font-family: 'Open Sans', sans-serif;
      font-size:40px;
      font-weight:600;
      color:black;
  }
  #HeaderSeparator{
      background-color:rgba(0,0,0,0.1);
      width:100%;
      position:absolute;
      left:0%;
      top:12%;
      height:2px;
  }
  #RightSeparator{
      background-color:rgba(0,0,0,0.1);
      height:88%;
      position:absolute;
      left:75%;
      top:12%;
		width:2px;
  }
  #Map{
	height:100%;
	position:absolute;
	top:0%;
	left:30%;
	
  }
  #BoxContainer{
	height:100%;
	position:absolute;
	top:0%;
	left:30%;
	width:952px;
  }
  #ViewSelector{
	border:2px solid rgba(0,0,0,0.1);
	position:absolute;
	left:2%;
	top:65%;
	width:10%;
	height:30%;
	border-radius:5px;
  }
  #ClubsView{
	width:100%;
	border-bottom:2px solid rgba(0,0,0,0.1);
	height:25%;
	position:absolute;
	left:0%;
	top:0%;
	background-color:#c2ffd3;
	color:black;
	
	font-family: 'Open Sans', sans-serif;
	border-right:none;
	border-top:none;
	border-left:none;
	font-size:25px;
	font-weight:500;
	cursor:pointer;
	transition:0.1s all;
  }
  
  #LunchView{
	width:100%;
	border-bottom:2px solid rgba(0,0,0,0.1);
	height:25%;
	position:absolute;
	left:0%;
	top:25%;
	background-color:rgba(100,100,100,0.05);
	font-family: 'Open Sans', sans-serif;
	border-right:none;
	border-top:none;
	border-left:none;
	font-size:25px;
	font-weight:500;
	cursor:pointer;
	transition:0.1s all;
  }
  
  #TeachersView{
	width:100%;
	border-bottom:2px solid rgba(0,0,0,0.1);
	height:25%;
	position:absolute;
	left:0%;
	top:50%;
	background-color:rgba(100,100,100,0.05);
	font-family: 'Open Sans', sans-serif;
	border-right:none;
	border-top:none;
	border-left:none;
	font-size:25px;
	font-weight:500;
	cursor:pointer;
	transition:0.1s all;
  }
   
  .notSelected:hover{
	filter:brightness(70%);
  }
  #EventsView{
	width:100%;
	border-bottom:none;
	height:25%;
	position:absolute;
	left:0%;
	top:75%;
	background-color:rgba(100,100,100,0.05);
	font-family: 'Open Sans', sans-serif;
	border-right:none;
	border-top:none;
	border-left:none;
	font-size:25px;
	font-weight:500;
	cursor:pointer;
	transition:0.1s all;
  }
   
  #ViewLabel{
	position:absolute;
	width:100%;
	text-align:center;
	top:-15%;
	font-family: 'Open Sans', sans-serif;
	font-size:20px;
	font-weight:500;
	opacity:0;
  }


</style>
  
  