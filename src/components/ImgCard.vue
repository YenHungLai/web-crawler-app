<template>
	<div class="card-container">
		<img :src="content.url" :alt="content.filename" />
		<div class="description">
			<p>
				<strong>Filename:</strong>
				{{content.filename}}
			</p>
			<a :href="content.url" target="_blank" v-text="content.url"></a>
		</div>
	</div>
</template>

<script>
export default {
	name: "ImgCard",
	props: ["content"]
};
</script>

<style scoped>
.card-container {
	display: flex;
	justify-content: space-between;
	margin: 0 0 1em 0;
	padding: 0.5em 1em;
	box-shadow: 0 1px 2px rgba(0, 0, 0, 0.16), 0 1px 1px rgba(0, 0, 0, 0.23);
	background-color: white;
	font-style: italic;
}
img {
	max-height: 100%;
	max-width: 50%;
}
.description {
	display: flex;
	flex-direction: column;
	justify-content: flex-start;
	margin-left: 2em;
	overflow: hidden;
}
.description > * {
	overflow: hidden;
	text-overflow: ellipsis;
	white-space: nowrap;
}
</style>