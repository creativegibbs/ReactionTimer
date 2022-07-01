<template>
	<p class="results">U Reactietijd Score is: {{ score }} ms</p>
	<p class="rang">Uw Rang: {{ rank }}</p>
	<div v-if="this.score < 250">
		<img :src="urlm" alt="" />
	</div>
	<div v-else="this.score > 250">
		<img :src="url" alt="" />
	</div>

	<!-- <p>{{ title }}</p> -->
</template>

<script>
export default {
	props: ["score"],
	data() {
		return {
			url: "https://image.shutterstock.com/image-vector/white-guy-rastaman-beard-glasses-600w-1704141712.jpg",
			urlm: "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fposterspy.com%2Fwp-content%2Fuploads%2F2019%2F03%2Fmatrix-neo-pinterest.jpg&f=1&nofb=1",
			rank: 0,
			music:""
		};
	},
	// methods: {
	// 	playingSound(){
	// 		const music = new Audio('high.mp3');
	// 	music.play();
	// 	}
	// }

	mounted() {
		let file = "default file";
		if (this.score < 250) {
			this.rank = "Congratz YOU ESCAPED THE MATRIX";
			file = require("@/assets/matrixbaby.mp3");
		} else if (this.score < 400) {
			this.rank =
				"BloodClat Rapid Reflexes You still need to practice some more";
			file = require("@/assets/high.mp3");
		} else {
			this.rank =
				"Afro Man you need to stop getting High and press the button Faster!";
			file = require("@/assets/high.mp3");
		}

		this.music = new Audio(file);
		this.music.play();
		this.music.controls = true;
		this.music.loop = true;
		this.music.playbackRate = 1;
	},

	unmounted() {
		this.music.pause();
		console.log("unmounted");
	},
};
</script>

<style>
.results {
	font-weight: 500;
	border: 1px solid grey;
	width: 300px;
	font-size: 2rem;
	margin: 20px auto;
	padding: 0 0.5rem;
}

.rang {
	margin-top: 20px;
	font-size: 1.5rem;
	margin: 50px auto;
	background-color: rgb(29, 69, 29);
	color: aliceblue;
	padding: 0 0.5rem;
	margin-bottom: 20px;
}

img {
	margin: 0 auto;
	/* width: 100%; */
	max-width: 70%;
	height: 500px;
}
</style>
