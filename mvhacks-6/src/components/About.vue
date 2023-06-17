<template>
    <router-link to="/" id="Home">MVHS Logistic Map</router-link>
    <VButton x="80%" y="3%" width="120px" height="60px" text="About" fontSize="25px" styl="secondary" borderRadius="10px" @click = "goToAbout"></VButton>
    <VButton x="90%" y="3%" width="120px" height="60px" text="Map" fontSize="25px" styl="normal" borderRadius="10px" @click = "goToMap"></VButton>
    <div id="HeaderSeparator"></div>
    <h1>About Us</h1>
    <p>Lorem Ipsum，也称乱数假文或者哑元文本， 是印刷及排版领域所常用的虚拟文字。由于曾经一台匿名的打印机刻意打乱了一盒印刷字体从而造出一本字体样品书，Lorem Ipsum从西元15世纪起就被作为此领域的标准文本使用。它不仅延续了五个世纪，还通过了电子排版的挑战，其雏形却依然保存至今。在1960年代，”Leatraset”公司发布了印刷着Lorem Ipsum段落的纸张，从而广泛普及了它的使用。最近，计算机桌面出版软件”Aldus PageMaker”也通过同样的方式使Lorem Ipsum落入大众的视野。</p>
  </template>
  <script>
  import VButton from "./VButton.vue";
  export default {
      components:{
          VButton,
      },
      methods:{
          goToAbout(){
              window.location.href = "/about";
          },
		  goToMap(){
            window.location.href = "/map";
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
  </style>
  
  