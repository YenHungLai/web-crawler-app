<template>
	<div id="app">
		<Landing v-show="showLanding" @remove-landing="showLanding = false" />
		<Home v-if="!showLanding" @show-landing="revealLanding" />
	</div>
</template>

<script>
import Landing from "./components/Landing";
import Home from "./components/Home";

export default {
	name: "app",
	components: {
		Landing,
		Home
	},
	data() {
		return {
			showLanding: true
		};
	},
	methods: {
		revealLanding() {
			this.showLanding = true;
			document.querySelector(".landing-container").style.opacity = "1";
		}
	}
};
</script>

<style>
body {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	overflow-x: hidden;
}
</style>
