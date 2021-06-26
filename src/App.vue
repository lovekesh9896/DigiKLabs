<template>
	<div class="container">
		<Navigation
			@navigation-selected="handleNavigation"
			:restaurents="restaurents"
		/>
		<Categories :showAll="showAll" :restaurents="restaurents" />
	</div>
</template>

<script>
import Navigation from "./components/Navigation.vue";
import Categories from "./components/Categories.vue";

export default {
	name: "App",
	components: {
		Navigation,
		Categories,
	},
	data() {
		return {
			restaurents: [],
			showAll: false,
		};
	},
	methods: {
		async fetachData() {
			let res = await fetch(
				"https://mocki.io/v1/3fb1488d-bbdb-4ddd-9a03-a0d2efc98597"
			);
			let json = await res.json();
			// add extra category only on swiggy
			let allResArr = [];
			for (let i = 0; i < json.length; i++) {
				for (let j = 0; j < json[i].restaurantList.length; j++) {
					if (json[i].restaurantList[j].isExlusive) {
						allResArr.push(json[i].restaurantList[j]);
					}
				}
			}
			let onlyOnSwiggy = {
				category: "Only on swiggy",
				restaurantList: allResArr,
			};
			json = [...json, onlyOnSwiggy];
			return json;
		},
		handleNavigation(index) {
			// when show all restaurents is clicked
			if (index == 5 && !this.showAll) {
				this.showAll = true;
				window.scrollTo(0, 0);
			} else if (index != 5 && this.showAll) {
				this.showAll = false;
			}
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
	scroll-behavior: smooth;
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
