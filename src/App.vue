<template>
  <h1 id="phonemsg">
    Dear sorcerer, please come back on a computer to fully enjoy the experience.
  </h1>
  <div id="home">
    <video autoplay muted loop id="dragvid">
      <source src="./assets/dragvid4.mp4" type="video/mp4" />
    </video>
    <header>
      <div id="socials">
        <a target="_blank" href="https://twitter.com/AvaxWnd"><img id="twi" src="./assets/twi.png" /></a>
        <a target="_blank" href="https://discord.gg/6cXDfcDaR5"><img id="disc" src="./assets/disc.png" /></a>
        <a target="_blank" href=""><img id="ope" src="./assets/nft.png" /></a>
        <a target="_blank" href=""><img id="scan" src="./assets/scan.png" /></a>
      </div>
      <div id="wallet">
        <button id="conWallet" @click="changeMessage(connecting)">{{ connectMessage }}</button>
      </div>
    </header>
    <section>
      <div id="text">
		<div id="stakingOn">
			<h1>Choose the units who will defend your lands</h1>
			<div id="stakingBox">
			<h2>Wizards :</h2>
			<div id="boxStake1">
			<h3><button class="numberButton" @click="changeStakeWizard(0)">-</button></h3>
			<h3 id="nMint">{{ toStakeWizards }}</h3>
			<h3><button class="numberButton" @click="changeStakeWizard(1)">+</button></h3>
			</div>
			<h2>Dragons :</h2>
			<div id="boxStake2">
			<h3><button class="numberButton" @click="changeStakeDrake(0)">-</button></h3>
			<h3 id="nMint">{{ toStakeDragons }}</h3>
			<h3><button class="numberButton" @click="changeStakeDrake(1)">+</button></h3>
			</div>
			</div>
			<button id="doneButton">done</button>
		</div>
		<div id="afterMint">
			<div id="leftPart">
				<h1>UnStaked</h1>
				<h2>Wizards : {{ unstakedWizards }}</h2>
				<h2>Dragons : {{ unstakedDragons }}</h2>
				<button id="stakeButton">STAKE AND DEFEND !</button>
				<h3>Select your NFTs to Stake</h3>
			</div>
			<div id="middlePart">
				<h1>Defend The Land</h1>
				<h2>(STAKE) TO EARN $aGP</h2>
				<img src="./assets/dragcut.png">
				<h3>Balance : {{ awndValue }} $aGP</h3>
				<button id="mintMore">Mint More</button>
			</div>
			<div id="rightPart">
				<h1>Staked</h1>
				<h2>Defending The Land :<br /> {{ stakedWizards }} Wizards <br /> {{ stakedDragons }} Dragons</h2>
				<button id="claimButton">CLAIM $aGP !</button>
				<button id="claimAndUnstakeButton">CLAIM $aGP <br />AND UNSTAKE !</button>
				<h2>unclamed : {{ unclaimedAwnd }} $aGP</h2>
				<h3>Select your NFTs to claim rewards</h3>
			</div>
		</div>
		<div id="mintOn">
		<h1>Minting</h1>
		<h3 id="descMint">Your valuable gold pieces may now be placed onto the transmutation table</h3>
		<h2>{{ actualSupply }}/{{ totalSupply }} Minted</h2>
		<h2>Progression: {{ progression }}</h2>
		<div id="boxCount">
			<button class="numberButton" @click="changeMint(0)">-</button>
			<h3 id="nMint">{{ mintNumber }}</h3>
			<button class="numberButton" @click="changeMint(1)">+</button>
		</div>
		<button id="mButton" @click="mintMethod()">Mint Now</button>
		<h2>Price : {{ actualPrice }} $AVAX</h2>
		</div>
		<div id="noMint">
        <h1 id="mintTitle">Wizards and Dragons</h1>
        <div id="mint">
          <a id="mintbut">Mint</a>
        </div>
		</div>
      </div>
      <div id="underbox">
        <div id="box1" class="box">
          <h1>Wizards</h1>
          <img src="./assets/wizard.png" />
          <h2>DEFEND THE LAND!</h2>
          <h3>Join the Guild and earn $AWND</h3>
        </div>
        <div id="box2" class="box">
          <h1>Dragons</h1>
          <img src="./assets/dragon.png" />
          <h3>Dragons steal new mints & earn $AWND from wizards</h3>
        </div>
        <div id="box3" class="box">
          <h1>$aGP</h1>
          <h2>The currency of the world.</h2>
          <h3>$AVAX & $aGP are the ONLY way to mint new guards for your tower</h3>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "Compteur",
  data() {
		return{
			connecting: 0,
			connectMessage: "connect wallet",
			actualSupply: 100,
			totalSupply: 10000,
			progression: "GEN-0",
			mintNumber: 1,
			actualPrice: 2,
			unstakedWizards: 10,
			unstakedDragons: 10,
			awndValue: 1000,
			unclaimedAwnd: 300,
			stakedWizards: 2,
			stakedDragons: 10,
			toStakeWizards: 0,
			toStakeDragons: 0,
		}
  },
  computed: {
    totalStore() {
      return this.$store.state.total;
    },
  },
  methods: {
    changeMint(type) {
		if (type == 0)
		{
			if (this.mintNumber > 1)
				this.mintNumber--;
		}
		else
		{
			if (this.mintNumber < 10000)
				this.mintNumber++;
		}
	},
	changeMessage(type) {
		if (type == 1)
		{
			this.connectMessage = "connect wallet";
			this.connecting = 0;
		}
		else
		{
			this.connectMessage = "connection...";
			this.connecting = 1;
		}
	},
	mintMethod() {
		
	},
	changeStakeWizard(type){
		if(type == 0)
		{
			if (this.toStakeWizards > 0)
				this.toStakeWizards--;
		}
		else{
			if (this.unstakedWizards > this.toStakeWizards)
				this.toStakeWizards++;
		}
	},
	changeStakeDrake(type){
		if(type == 0)
		{
			if (this.toStakeDragons > 0)
				this.toStakeDragons--;
		}
		else{
			if (this.unstakedDragons > this.toStakeDragons)
				this.toStakeDragons++;
		}
	},
  },
};
window.onload=function(){
let mintButton = document.querySelector("#mintbut");
let homeWindow = document.querySelector("#noMint");
let mintWindow = document.querySelector("#mintOn");
let	mButton = document.querySelector("#mButton");
let afterMintWindow = document.querySelector("#afterMint");
let mintMore = document.querySelector("#mintMore");
let doneButton = document.querySelector("#doneButton");
let stakeButton = document.querySelector("#stakeButton");
let stakingOn = document.querySelector("#stakingOn");
mintButton.addEventListener("click", function(){
	homeWindow.style.display="none";
	mintWindow.style.display="flex";
}),
mButton.addEventListener("click", function() {
	mintWindow.style.display="none";
	afterMintWindow.style.display="flex";
}),
mintMore.addEventListener("click", function() {
	mintWindow.style.display="flex";
	afterMintWindow.style.display="none";
}),
stakeButton.addEventListener("click", function() {
	afterMintWindow.style.display="none";
	stakingOn.style.display="flex";
}),
doneButton.addEventListener("click", function() {
	stakingOn.style.display="none";
	afterMintWindow.style.display="flex";
})
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css?family=Poppins:300,400,500,600,700,800,900&display=swap");
@font-face {
  font-family: "drake";
  src: url("./font/royal.ttf");
}
@font-face {
  font-family: "futura";
  src: url("./font/futur.ttf");
}
@font-face {
  font-family: "cotton";
  src: url("./font/coco.ttf");
}
@font-face {
  font-family: "flower";
  src: url("./font/flower.ttf");
}
@font-face {
  font-family: "gernika";
  src: url("./font/Gernika.otf");
}
@font-face {
  font-family: "fab";
  src: url("./font/fab.ttf");
}
#phonemsg {
  display: none;
}
#home {
  cursor: url("data:image/svg+xml,%3Csvg version='1.1' id='Layer_1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' x='0px' y='0px' width='24px' height='24px' viewBox='0 0 512 512' style='enable-background:new 0 0 512.011 512.011;' xml:space='preserve'%3E %3Cpath fill='black' d='M434.215,344.467L92.881,3.134c-4.16-4.171-10.914-4.179-15.085-0.019  c-2.011,2.006-3.139,4.731-3.134,7.571v490.667c0.003,4.382,2.685,8.316,6.763,9.92c4.081,1.603,8.727,0.545,11.712-2.667  l135.509-145.92h198.016c5.891,0.011,10.675-4.757,10.686-10.648C437.353,349.198,436.226,346.473,434.215,344.467z'/%3E %3C/svg%3E"),
    pointer;
}
a:hover, button:hover{
  cursor: url("data:image/svg+xml,%3Csvg version='1.1' id='Layer_1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' x='0px' y='0px' width='24px' height='24px' viewBox='0 0 512 512' style='enable-background:new 0 0 512.011 512.011;' xml:space='preserve'%3E %3Cpath fill='black' d='M434.215,344.467L92.881,3.134c-4.16-4.171-10.914-4.179-15.085-0.019  c-2.011,2.006-3.139,4.731-3.134,7.571v490.667c0.003,4.382,2.685,8.316,6.763,9.92c4.081,1.603,8.727,0.545,11.712-2.667  l135.509-145.92h198.016c5.891,0.011,10.675-4.757,10.686-10.648C437.353,349.198,436.226,346.473,434.215,344.467z'/%3E %3C/svg%3E"),
    pointer;
}
header {
  display: flex;
  justify-content: space-between;
}
#socials img:hover {
  cursor: url("data:image/svg+xml,%3Csvg version='1.1' id='Layer_1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' x='0px' y='0px' width='24px' height='24px' viewBox='0 0 512 512' style='enable-background:new 0 0 512.011 512.011;' xml:space='preserve'%3E %3Cpath fill='white' d='M434.215,344.467L92.881,3.134c-4.16-4.171-10.914-4.179-15.085-0.019  c-2.011,2.006-3.139,4.731-3.134,7.571v490.667c0.003,4.382,2.685,8.316,6.763,9.92c4.081,1.603,8.727,0.545,11.712-2.667  l135.509-145.92h198.016c5.891,0.011,10.675-4.757,10.686-10.648C437.353,349.198,436.226,346.473,434.215,344.467z'/%3E %3C/svg%3E"),
    pointer;
}
#stakingOn{
	display: none;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	text-align: center;
}
#stakingOn h1{
	margin: 0;
	font-family: gernika;
	color: white;
}
#stakingOn h2{
	color: rgba(177, 0, 0, 0.5);
	font-size: 0.7em;
	margin-bottom: 0px;
	margin: 0px;
	font-family: Poppins;
}
#doneButton{
	font-family: gernika;
	color: white;
}
#stakingOn button:hover{
	background: rgba(177, 0, 0, 0.5);
}
#stakingOn button{
	background: transparent;
	border: 3px rgba(177, 0, 0, 0.5) solid;
	border-radius: 70px;
	width: 200px;
	height: 70px;
	font-size: 1em;
}
#stakingOn h3{
	font-size: 1em;
	margin: 0;
	margin-left: 15px;
	margin-right: 15px;
}
#boxStake1, #boxStake2{
	display: flex;
	justify-content: center;
	height: 70px;
}
#stakingBox{
	display: flex;
	flex-direction: column;
}
#middlePart, #leftPart, #rightPart{
	width: 300px;
	display: flex;
	flex-direction: column;
	align-items: center;
	text-align: center;
}
#mintMore{
	height: 70px;
	width: 200px;
	font-size: 0.5em;
	margin-top: 20px;
}
#afterMint{
	display: none;
	justify-content: center;
}
#afterMint li{
	list-style: none;
}
#leftPart h1, #rightPart h1{
	font-size: 1.1em;
	font-family: gernika;
	color: rgb(255, 103, 103);
	text-decoration: underline;
	line-height: 0.4em;
}
#middlePart h1{
	text-decoration: underline;
	font-size: 1.1em;
	font-family: gernika;
	color: rgb(255, 103, 103);
	line-height: 0.9em;
}
#afterMint h2{
	font-size: 0.5em;
	margin: 0;
	margin-bottom: 20px;
	font-family: fab;
}
#afterMint h3{
	font-family: fab;
	font-size: 0.5em;
	margin: 0;
}
#leftPart button, #rightPart button{
	margin: 0;
	margin-bottom: 15px;
}
#mintTitle{
	font-family: cotton;
	line-height: 1em;
	font-size: 1.5em;
}
#afterMint button{
	background: transparent;
	border: 3px solid white;
	color: white;
	border-radius: 60px;
	font-family: gernika;
	font-size: 0.6em;
	line-height: 1em;
}
#claimButton, #stakeButton{
	height: 70px;
	width: 270px;
	font-size: 0.5em;
}
#claimAndUnstakeButton{
	height: 75px;
	width: 270px;
	font-size: 0.5em;
}
#afterMint button:hover{
	background: rgba(255, 255, 255, 0.9);
	color: black;
}
#mButton{
	background: transparent;
	width: 300px;
	height: 100px;
	border-radius: 60px;
	border: 2px white solid;
	color: white;
	font-size: 1em;
	font-family: gernika;
	line-height: 1em;
}
#mintOn button:hover{
	background: white;
	color: black;
}
#nMint{
	color: white;
}
#boxCount{
	width: 200px;
	display: flex;
	justify-content: space-around;
}
#mintOn{
	display: none;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	text-align: center;
}
#descMint{
	color: rgb(109, 109, 109);
}
.numberButton{
	width: 50px;
	height: 50px;
	font-size: 1em;
	background: transparent;
	border: 3px white solid;
	border-radius: 100px;
	color: white;
}
#mintOn h1{
	font-size: 1.4em;
	font-family: flower;
	line-height: 1.5em;
	margin-bottom: 10px;
}
#mintOn h3{
	font-size: 0.7em;
	margin-bottom: 10px;
	font-family: gernika;
}
#mintOn h2{
	font-family: fab;
	font-size: 0.6em;
	margin-bottom: 0;
	color: rgb(255, 103, 103);
}
#mintOn h3, #mintOn h2, #mintOn h1, #mintOn button{
	margin-top: 5px;
}
#conWallet {
  -webkit-appearance: button;
  -moz-appearance: button;
  appearance: button;
  font-family: "Poppins";
  font-size: 1.2em;
  width: 200px;
  height: 50px;
  color: white;
  background: transparent;
  border: 2px rgb(255, 255, 255) solid;
  border-radius: 30px;
  text-decoration: none;
  display: flex;
  justify-content: center;
  align-items: center;
}
#conWallet:hover {
  background: white;
  color: black;
}
#dragvid {
  position: absolute;
  height: 118%;
  width: 118%;
  top: 0;
  left: -200px;
  overflow: hidden;
  position: fixed;
  object-fit: cover;
  z-index: -1;
}
section {
  font-family: futura;
  font-size: 3em;
  color: #e6e6e6;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 10px;
}
#text {
  border-radius: 50px;
  background: rgba(0, 0, 0, 0.5);
  width: 1000px;
  height: 500px;
}
#noMint{
	display: flex;
	flex-direction: column;
	justify-content: flex-start;
	align-items: center;
}
#mintbut {
  -webkit-appearance: button;
  -moz-appearance: button;
  appearance: button;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: futura;
  font-size: 2em;
  letter-spacing: 0.3em;
  color: #ececec;
  height: 100px;
  width: 400px;
  background: transparent;
  border: 2px rgb(228, 228, 228) solid;
  border-radius: 30px;
}
#mintbut:hover {
  background: rgba(180, 180, 180, 0.3);
}
@keyframes color-change {
  0% {
    color: rgb(0, 0, 0);
  }
  50% {
    color: rgb(255, 255, 255);
  }
  100% {
    color: rgb(0, 0, 0);
  }
}
#twi {
  position: relative;
  height: 40px;
  width: 50px;
  top: -30px;
  margin-right: 5px;
}
#disc {
  position: relative;
  top: -25px;
  height: 50px;
  width: 50px;
  margin-right: 12px;
}
#ope {
  position: relative;
  top: -45px;
  height: 15px;
  width: 100px;
}
#scan {
  position: relative;
  top: -10px;
  height: 80px;
  width: 80px;
}
#underbox {
  width: 1300px;
  display: flex;
  justify-content: space-between;
}
.box {
  width: 400px;
  height: 300px;
  border-radius: 50px;
  border: 1px black solid;
  background: rgba(0, 0, 0, 0.5);
}
.box {
  font-family: cotton;
  line-height: 1em;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 30px;
  text-align: center;
}
.box h1 {
  font-size: 1.2em;
  letter-spacing: 10px;
  margin: 0;
}
.box h2 {
  font-size: 0.5em;
  margin: 0;
}
.box h3 {
  margin-top: 10px;
  font-size: 0.4em;
}
#underbox h2,
#underbox h3 {
  font-family: Poppins;
}
@media screen and (max-width: 1200px) {
  #home {
    display: none;
  }
  #phonemsg {
    display: block;
    font-size: 2em;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 400px;
    text-align: center;
  }
}
@media screen and (max-width: 800px) {
  #home {
    display: none;
  }
  #phonemsg {
    display: block;
    font-size: 1.5em;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 400px;
    text-align: center;
  }
}
@media screen and (max-width: 500px) {
  #home {
    display: none;
  }
  #phonemsg {
    display: block;
    font-size: 1em;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 300px;
    text-align: center;
  }
}
</style>
