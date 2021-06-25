<template>
	<div class="item-card">
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

.item-card:hover {
	border-color: #d3d5df;
	box-shadow: 0 4px 7px 0 rgb(218 220 230 / 60%);
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
.item-card:hover .item-card__quick-view {
	opacity: 1;
}
</style>
