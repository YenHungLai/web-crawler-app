<template v-if='content.value'>
	<div class="content-area-container" v-if="content.key === 'title'">
		<Card v-if="content.value">
			<p v-text="content.value"></p>
		</Card>
		<h2 v-else>Oops could not find anything!</h2>
	</div>
	<div class="content-area-container" v-else-if="content.key === 'favicon'">
		<Card v-if="content.value">
			<img :src="content.value" :alt="content.value" />
		</Card>
		<h2 v-else>Oops could not find anything!</h2>
	</div>
	<div class="content-area-container" v-else-if="content.key === 'images'">
		<ImgCard v-for="(entry, index) in content.value" :key="index" :content="entry" />
	</div>
	<div class="content-area-container" v-else-if="content.key === 'links'">
		<Card v-for="(entry, index) in content.value" :key="index">
			<a :href="entry" target="_blank">{{entry}}</a>
		</Card>
	</div>
	<div class="content-area-container" v-else-if="arrayTypes.includes(content.key)">
		<Card v-for="(entry, index) in content.value" :key="index">
			<p v-text="entry"></p>
		</Card>
		<h2 v-show="content.value.length === 0">Oops could not find anything!</h2>
	</div>
</template>

<script>
import Card from "./Card.vue";
import ImgCard from "./ImgCard.vue";

export default {
	name: "ContentArea",
	components: {
		Card,
		ImgCard
	},
	props: ["content"],
	data() {
		return {
			arrayTypes: ["h1", "h2", "h3", "p"]
		};
	}
};
</script>

<style scoped>
.content-area-container {
	overflow-y: auto;
	max-height: 69%;
	margin: 1em 0;
	padding-right: 1em;
	max-width: 80%;
	font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

/* FIXME: it appears when content is not overflowing */
.content-area-container::-webkit-scrollbar-track {
	-webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
	background-color: #f5f5f5;
	border-radius: 10px;
}

.content-area-container::-webkit-scrollbar {
	width: 10px;
	background-color: #f5f5f5;
}

.content-area-container::-webkit-scrollbar-thumb {
	height: 100px;
	border-radius: 10px;
	background-color: #8d9ae0;
}
</style>