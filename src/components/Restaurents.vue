<template>
	<div v-bind:id="category.category" class="one-category">
		<h3>
			{{ category.category }}
		</h3>
		<div class="restaurents">
			<div
				class="res-container"
				:key="index"
				v-for="(restau, index) in category.restaurantList"
			>
				<Restaurent v-if="index < currShowNumber" :res="restau" />
				<OneResExtra
					@load-more="loadMore"
					v-if="index == currShowNumber"
					:res="restau"
					:itemsLeft="category.restaurantList.length - currShowNumber"
				/>
			</div>
		</div>
	</div>
</template>

<script>
import Restaurent from "./OneRestaurent.vue";
import OneResExtra from "./OneResExtra.vue";

export default {
	name: "Restaurents",
	props: {
		category: Object,
	},
	data() {
		return {
			currShowNumber: 5,
		};
	},
	components: {
		Restaurent,
		OneResExtra,
	},
	methods: {
		loadMore() {
			this.currShowNumber += 3;
		},
	},
};
</script>

<style scoped>
.one-category {
	display: flex;
	flex-direction: column;
	text-align: left;
}

.restaurents {
	display: flex;
	flex-wrap: wrap;
}

h3 {
	margin-left: 24px;
}
</style>
