<template>
	<div class="content-area-container" v-if="content.key === 'title'">
		<Card>
			<p v-text="content.value"></p>
		</Card>
	</div>
	<div class="content-area-container" v-else-if="content.key === 'favicon'">
		<Card>
			<img :src="content.value" :alt="content.value" />
		</Card>
	</div>
	<div class="content-area-container" v-else-if="content.key === 'images'">
		<ImgCard v-for="(entry, index) in content.value" :key="index" :content="entry" />
	</div>
	<div class="content-area-container" v-else-if="arrayTypes.includes(content.key)">
		<Card v-for="(entry, index) in content.value" :key="index">
			<p v-text="entry"></p>
		</Card>
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
			arrayTypes: ["h1", "h2", "h3", "links", "p"]
		};
	}
};
</script>

<style scoped>
.content-area-container {
	overflow-y: scroll;
	height: 50%;
	margin: 1em 0;
	max-width: 80%;
}
</style>