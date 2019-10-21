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
        <slot></slot>
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
	font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
	box-shadow: 0 1px 2px rgba(0, 0, 0, 0.16), 0 1px 1px rgba(0, 0, 0, 0.23);
	background-color: white;
	font-style: italic;
	padding: 0.5em 1em;
	margin: 1em 0;
	display: flex;
	justify-content: space-between;
}
img {
	height: 250px;
}
.description {
	display: flex;
	flex-direction: column;
	justify-content: flex-start;
}
</style>