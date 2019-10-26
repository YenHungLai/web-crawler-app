<template>
	<div class="landing-container">
		<button @click="start">get started</button>
		<img alt="robot" src="../assets/robot.png" />
	</div>
</template>

<script>
export default {
	name: "Landing",
	methods: {
		start(e) {
			// Make landing page disappear
			this.$emit("remove-landing");
			document.querySelector(".landing-container").style.opacity = "0";
			setTimeout(() => {
				document.querySelector(".landing-container").style.display =
					"none";
			}, 500);
		}
	}
};
</script>

<style scoped>
.landing-container {
	height: 100vh;
	display: flex;
	justify-content: center;
	align-items: center;
	transition: all 0.5s ease-in;
	background: url("../assets/background.jpg") no-repeat right;
	background-size: cover;
}
.landing-container button {
	display: inline-block;
	padding: 0.7em 1.4em;
	margin: 0 0.3em 0.3em 0;
	border-radius: 0.15em;
	border: none;
	text-decoration: none;
	text-transform: uppercase;
	font-weight: bold;
	color: #ffffff;
	background-color: #3369ff;
	box-shadow: 0.15em 0.3em #3369ffbd;
	text-align: center;
	outline: none;
	cursor: pointer;
}
.landing-container button:active {
	transform: translateY(2px);
}
img[alt="robot"] {
	width: 25%;
	mix-blend-mode: multiply;
}

@media only screen and (max-width: 815px) {
	.landing-container {
		flex-direction: column-reverse;
		padding-right: 20%;
	}
	img[alt="robot"] {
		width: 45%;
		mix-blend-mode: multiply;
	}
}
</style>