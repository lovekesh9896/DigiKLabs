<template>
	<div @click="$emit('load-more')" class="item-card">
		<div class="card-overlay">+{{ itemsLeft }} MORE</div>
		<img
			src="https://images.unsplash.com/photo-1484723091739-30a097e8f929?auto=format&fit=crop&w=500&q=60"
			alt=""
			class="item-thumb"
		/>
		<div class="item-card-content">
			{{ res.name }}
			<div class="item-card__tags">
				<div
					class="item-card__tag"
					:key="tag"
					v-for="tag in res.food_types"
				>
					{{ tag }}
				</div>
			</div>
			<div class="item-card__stats-row">
				<div
					:class="[
						res.ratings !== ''
							? 'item-card__star-wrap --green'
							: 'item-card__star-wrap ',
					]"
				>
					★ {{ res.ratings === "" ? "--" : res.ratings }}
				</div>
				<div>•</div>
				<div class="item-card__delivery-time">
					{{ res.delivery_time }}
				</div>
				<div>•</div>
				<div class="item-card__price">
					₹{{ res.price_for_two }} FOR TWO
				</div>
			</div>
			<div class="item-card__quick-view">QUICK VIEW</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "OneRestaurent",
	props: {
		res: Object,
		itemsLeft: Number,
	},
};
</script>

<style scoped>
.item-card {
	background-color: #fff;
	border: 1px solid hsla(0, 0%, 100%, 0);
	margin: 8px;
	width: 260px;
	position: relative;
	padding: 16px;
	cursor: pointer;
}

.card-overlay {
	position: absolute;
	z-index: 10;
	background: rgba(255, 255, 255, 0.9);
	display: flex;
	color: red;
	border: 2px solid;
	width: 90%;
	height: 90%;
	top: 5%;
	left: 5%;
	justify-content: center;
	align-items: center;
	font-size: 2rem;
}

.item-card .item-thumb {
	width: 100%;
	height: 120px;
	object-fit: cover;
}
.item-card .item-card-content {
	margin-top: 8px;
	text-align: left;
	font-size: 14px;
}

.item-card__tags {
	display: -webkit-flex;
	display: flex;
	-webkit-align-items: center;
	align-items: center;
	-webkit-flex-wrap: wrap;
	flex-wrap: wrap;
	margin-top: 4px;
	height: 32px;
	overflow: hidden;
}
.item-card__tags .item-card__tag {
	padding: 2px 8px;
	background-color: #ececec;
	margin: 4px;
	font-size: 12px;
	border-radius: 20px;
	color: #373737;
	cursor: pointer;
	opacity: 0.6;
}
.item-card__stats-row {
	display: -webkit-flex;
	display: flex;
	-webkit-align-items: center;
	align-items: center;
	-webkit-justify-content: space-between;
	justify-content: space-between;
	font-size: 12px;
	color: #979797;
	margin-top: 16px;
}
.item-card__stats-row .item-card__star-wrap.--green {
	background-color: #48c479;
	color: #fff;
}
.item-card__stats-row .item-card__star-wrap {
	padding: 2px 6px;
	border-radius: 2px;
}
.item-card__quick-view {
	font-size: 14px;
	border-top: 1px solid #e9e9eb;
	padding-top: 14px;
	margin-top: 14px;
	font-weight: 500;
	text-align: center;
	color: #5d8ed5;
	opacity: 0;
}
</style>
