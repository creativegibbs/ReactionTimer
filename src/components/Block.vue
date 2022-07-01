<template>
	<div class="block" v-if="showBlock" @click="stopTimer">
		<p>Click Me Monnn<i class="fa-solid fa-computer-mouse"></i></p>
	</div>
</template>

<script>
export default {
	props: ["delay"],
	data() {
		return {
			showBlock: false,
			timer: null,
			reactionTime: 0,
		};
	},
	mounted() {
		console.log("component mounted");
		setTimeout(() => {
			this.showBlock = true;
			this.startTimer();
			console.log(this.delay);
		}, this.delay);
	},

	methods: {
		startTimer() {
			this.timer = setInterval(() => {
				this.reactionTime += 10;
			}, 10);
		},

		stopTimer() {
			clearInterval(this.timer);
			this.$emit("end", this.reactionTime);
			// console.log("timer has been stopped");
			// console.log(this.reactionTime);
		},
	},
	// updated() {
	// 	console.log("Component Updated");
	// },

	// unmounted() {
	// 	console.log("Component Unmounted");
	// },
};
</script>

<style>
.block {
	width: 100%;
	height: 200px;
	border-radius: 20px;
	background-color: rgb(45, 94, 110);
	color: white;
	display: flex;
	justify-content: center;
	align-items: center;
	padding: 100px 0;
	margin: 40px auto;
}

.block p {
	font-size: 2rem;
}

i {
	margin-left: 10px;
}
</style>
