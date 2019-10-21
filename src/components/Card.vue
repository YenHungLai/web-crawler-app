<template>
	<div class="card-container">
		<!-- <p v-text="content"></p> -->
        <slot></slot>
	</div>
</template>

<script>
export default {
	name: "Card",
	props: ["content"]
};
</script>

<style scoped>
.card-container {
	font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    box-shadow: 0 1px 2px rgba(0,0,0,0.16), 0 1px 1px rgba(0,0,0,0.23);
	background-color: white;
	font-style: italic;
    padding: 0.5em 1em;
    margin: 1em 0;
}
</style>