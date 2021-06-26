<template>
	<nav class="navigation">
		<div class="navigation-content">
			<ul>
				<li
					:class="[
						index == 0
							? 'navigation-li active-li'
							: 'navigation-li',
					]"
					@click="changeColor(index, e)"
					:key="index"
					v-for="(res, index) in restaurents"
				>
					<a v-bind:href="`#${res.category}`">
						<div>
							{{ res.category }}
						</div>
						<small
							>{{ res.restaurantList.length }} Restaurents</small
						>
					</a>
				</li>
				<li
					class="navigation-li"
					@click="changeColor(restaurents.length, e)"
				>
					<a v-bind:href="`#show-all`">
						<div>
							All Restaurents
						</div>
						<small
							>{{
								calculateTotalRestaurents()
							}}
							Restaurents</small
						>
					</a>
				</li>
			</ul>
		</div>
	</nav>
</template>

<script>
export default {
	name: "Navigation",
	props: {
		restaurents: Array,
	},
	methods: {
		changeColor(index) {
			let navigationLi = document.getElementsByClassName("navigation-li");
			for (let i = 0; i < navigationLi.length; i++) {
				navigationLi[i].classList.remove("active-li");
			}
			navigationLi[index].classList.add("active-li");
			this.$emit("navigation-selected", index);
		},
		calculateTotalRestaurents() {
			// to show total number of restaurents
			let ans = 0;
			for (let i = 0; i < this.restaurents.length - 1; i++) {
				ans += this.restaurents[i].restaurantList.length;
			}
			return ans;
		},
	},
};
</script>

<style scoped>
.navigation {
	widows: 250px;
	text-align: left;
}

.navigation-content {
	position: sticky;
	top: 100px;
	border-top: 1px solid #eaeaea;
	border-left: 1px solid #eaeaea;
	border-right: 1px solid #eaeaea;
}

ul {
	list-style: none;
}

li {
	padding: 16px;
	text-transform: capitalize;
	cursor: pointer;
	border-bottom: 1px solid #eaeaea;
	min-width: 200px;
}
li:hover {
	background: #eee;
}
small {
	font-size: 12px;
	margin-top: 8px;
	opacity: 0.6;
}
a {
	color: inherit;
	text-decoration: none;
	padding-top: -40px;
}
.active-li {
	background-color: #fa4a5b;
	color: #fff;
}
.active-li:hover {
	background-color: #fa4a5b;
	color: #fff;
}
</style>
