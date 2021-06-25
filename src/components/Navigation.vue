<template>
	<nav class="navigation">
		<div class="navigation-content">
			<ul :key="restaurents.category" v-for="res in restaurents">
				<li>
					<div>
						{{ res.category }}
					</div>
					<small>{{ res.restaurantList.length }} Restaurents</small>
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
	color: grey;
	font-size: 12px;
	margin-top: 8px;
	opacity: 0.6;
}
</style>
