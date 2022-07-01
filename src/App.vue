<template>
	<div class="timer-div">
		<h1>Rasta Reaction Timer</h1>
		<button @click="start" :disabled="isPlaying">
			Play <i class="fa-solid fa-gamepad"></i>
		</button>
		<Block class="block" v-if="isPlaying" :delay="delay" @end="endGame" />
		<!-- <p v-if="showResults"></p> -->
		<Results v-if="showResults" :score="score" />
	</div>

	<!-- <audio ref="audio"      hidden="true">
<source src="@/assets/high.mp3" type="audio/mpeg">

		Your browser does not support the
		<code>audio</code> element.
	</audio> -->
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
	name: "App",
	components: {
		Block,
		Results,
	},
	data() {
		return {
			isPlaying: false,
			delay: null,
			score: null,
			showResults: false,
		};
	},
	mounted() {
		// const audio = document.querySelector("audio");
		// console.log(audio.play);
		// // //@ts-ignore
		// audio.play();
	},
	methods: {
		start() {
			this.delay = 2000 + Math.random() * 5000;
			this.isPlaying = true;
			this.showResults = false;

			// console.log(this.delay);
		},

		endGame(reactionTime) {
			this.score = reactionTime;
			this.isPlaying = false;
			this.showResults = true;
		},
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #444;
	margin-top: 60px;
	/* background-image: url(./assets/lionrass.jpg);
	background-position: center;
	background-repeat: no-repeat; */
	margin: 1rem;
}

h1 {
	font-size: 2rem;
	color: rgb(72, 10, 10);
	font-weight: 600;
	text-transform: uppercase;
}

.timer-div {
	min-width: 100%;
	height: 80vh;
}

button {
	width: 50%;
	height: 50px;
}

body {
	overflow: hidden;
}
</style>
