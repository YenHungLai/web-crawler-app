<template>
	<nav class="tabs">
		<div class="selector"></div>
		<a v-for="tabName in tabNames" :key="tabName" @click="selectTab">{{tabName}}</a>
	</nav>
</template>

<script>
export default {
	name: "Tabs",
	props: {
		tabNames: Array
	},
	methods: {
		selectTab(e) {
			this.$emit("selected-tab", { tab: e.target.innerText });
		}
	},
	mounted() {
		console.log(this.tabNames);
		const tabs = document.querySelectorAll(".tabs a");
		const selector = document.querySelector(".selector");
		tabs[0].classList.add("active");
		const active = document.querySelector(".active");
		const activeWidth = active.clientWidth;

		selector.style.left = active.style.left + "px";
		selector.style.width = activeWidth + "px";

		tabs.forEach(tab => {
			tab.addEventListener("click", e => {
				tabs.forEach(tab => {
					if (tab !== e.target) tab.classList.remove("active");
				});
				e.target.classList.add("active");
				selector.style.left = e.target.offsetLeft + "px";
			});
		});
	}
};
</script>

<style scoped>
.tabs {
	display: flex;
	width: 80%;
	position: relative;
	margin-top: 2em;
	list-style: none;
	background: #fff;
	box-shadow: 0px 5px 20px rgba(0, 0, 0, 0.1);
	border-radius: 50px;
}

.tabs a {
	display: inline-block;
	position: relative;
	padding: 0.625em 1.25em;
	flex: 1;
	z-index: 1;
	cursor: pointer;
	color: #777;
	text-decoration: none;
	text-transform: uppercase;
	text-align: center;
	transition: all 0.6s ease-in;
}

.tabs a.active {
	color: #fff;
}

.tabs .selector {
	height: 100%;
	display: inline-block;
	position: absolute;
	left: 0px;
	top: 0px;
	z-index: 1;
	border-radius: 50px;
	transition-duration: 0.6s;
	transition-timing-function: cubic-bezier(0.68, -0.55, 0.265, 1.55);

	background: #05abe0;
	background: -moz-linear-gradient(45deg, #05abe0 0%, #8200f4 100%);
	background: -webkit-linear-gradient(45deg, #05abe0 0%, #8200f4 100%);
	background: linear-gradient(45deg, #05abe0 0%, #8200f4 100%);
}
</style>