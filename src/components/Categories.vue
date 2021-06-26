<template>
	<div class="catogries">
		<div
			class="one-category"
			:key="index"
			v-show="!showAll"
			v-for="(category, index) in restaurents"
		>
			<Restaurents :category="category" />
		</div>
		<div class="one-category" v-show="showAll">
			<h3 v-show="showAll">All Restaurents</h3>
			<div class="restaurents">
				<template v-for="(cate, indexP) in restaurents">
					<div
						:key="index * 100"
						v-for="(oneres, index) in cate.restaurantList"
					>
						<OneRestaurent v-if="indexP != 5" :res="oneres" />
					</div>
				</template>
			</div>
		</div>
	</div>
</template>

<script>
import Restaurents from "./Restaurents.vue";
import OneRestaurent from "./OneRestaurent.vue";

export default {
	name: "Categories",
	components: {
		Restaurents,
		OneRestaurent,
	},
	props: {
		restaurents: Array,
		showAll: Boolean,
	},
};
</script>

<style scoped>
.catogries {
	scroll-behavior: smooth;
}
.one-category {
	display: flex;
	flex-direction: column;
	text-align: left;
	margin-bottom: 60px;
}

.restaurents {
	display: flex;
	flex-wrap: wrap;
}

h3 {
	margin-left: 24px;
}
</style>
