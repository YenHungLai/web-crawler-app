<template>
	<div class="home-container">
		<button class="base-btn back-btn" @click="goBack">
			<i class="fas fa-long-arrow-alt-left fa-2x"></i>
		</button>
		<form @submit.prevent="onSubmit">
			<input type="url" v-model="url" placeholder="Please enter an URL to crawl" />
			<button class="base-btn">Enter</button>
		</form>
		<Tabs v-if="response" :tabNames="tabNames" @selected-tab="selectTab" />
		<ContentArea
			v-if="selectedTab"
			:content="{key: selectedTab.toLowerCase(), value: response[selectedTab.toLowerCase()]}"
		/>
	</div>
</template>

<script>
import axios from "axios";
import Tabs from "./Tabs.vue";
import ContentArea from "./ContentArea.vue";

export default {
	name: "Home",
	components: {
		Tabs,
		ContentArea
	},
	data() {
		return {
			url: null,
			prevUrl: null,
			response: null,
			tabNames: [],
			selectedTab: null
		};
	},
	methods: {
		onSubmit() {
			if (this.url !== this.prevUrl)
				axios
					.get(
						`https://cors-anywhere.herokuapp.com/https://mighty-oasis-97765.herokuapp.com?url=${this.url}`
					)
					.then(res => {
						this.response = res.data;
						this.tabNames = Object.keys(this.response);
						console.log(this.response);
					});

			this.prevUrl = this.url;
		},
		goBack() {
			this.$emit("show-landing");
		},
		selectTab(payload) {
			this.selectedTab = payload.tab;
		}
	}
};
</script>

<style scoped>
.home-container {
	display: flex;
	flex-direction: column;
	align-items: center;
	height: 100vh;
	background-color: #d3d3d34a;
}
.home-container form {
	width: 35%;
	margin-top: 6%;
	display: flex;
	position: relative;
}
.home-container input {
	padding: 1em;
	outline: none;
	border: none;
	box-shadow: 0 6px 6px -5px black;
	flex: 1;
}

.base-btn {
	outline: none;
	border: none;
	background-color: rgba(35, 97, 255, 0.81);
	color: white;
	text-transform: uppercase;
	font-weight: bold;
	cursor: pointer;
}
.base-btn:active {
	transform: translateY(2px);
}
.base-btn:hover {
	opacity: 0.7;
}
.home-container form button {
	position: absolute;
	right: 0;
	height: 100%;
	width: 20%;
}

.back-btn {
	position: fixed;
	top: 10px;
	left: 15px;
	height: 2em;
	width: 4em;
}
</style>