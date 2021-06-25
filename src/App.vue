<template>
	<div class="container">
		<Navigation :restaurents="restaurents" />
		<Restaurents :restaurents="restaurents" />
	</div>
</template>

<script>
import Navigation from "./components/Navigation.vue";
import Restaurents from "./components/Restaurents.vue";
export default {
	name: "App",
	components: {
		Navigation,
		Restaurents,
	},
	data() {
		return {
			restaurents: [],
			showAddTask: false,
		};
	},
	methods: {
		async fetachData() {
			let res = await fetch(
				"https://mocki.io/v1/3fb1488d-bbdb-4ddd-9a03-a0d2efc98597"
			);
			let json = await res.json();
			return json;
		},
	},
	async created() {
		this.restaurents = await this.fetachData();
	},
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
	box-sizing: border-box;
	margin: 0;
	padding: 0;
}
body {
	font-family: "Poppins", sans-serif;
	text-align: center;
	margin-top: 100px;
}
.container {
	width: 100%;
	max-width: 1200px;
	margin: auto;
	padding: 0 32px;
	display: -webkit-flex;
	display: flex;
	-webkit-justify-content: space-between;
	justify-content: space-between;
	position: relative;
}
</style>
