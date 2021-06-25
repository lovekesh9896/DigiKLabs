<template>
	<div
		@dblclick="$emit('toggle-reminder', task.id)"
		:class="[task.reminder ? 'reminder' : '', 'task']"
	>
		<h3>
			{{ task.name }}
			<span @click="$emit('delete-task', task.id)" class="cross">X</span>
		</h3>
		<p>{{ task.delivery_time }}</p>
	</div>
</template>

<script>
export default {
	name: "Task",
	props: {
		task: Object,
	},
};
</script>

<style scoped>
.fas {
	color: red;
}
.task {
	background: #f4f4f4;
	margin: 5px;
	padding: 10px 20px;
	cursor: pointer;
}
.task.reminder {
	border-left: 5px solid green;
}
.task h3 {
	display: flex;
	align-items: center;
	justify-content: space-between;
}
.cross {
	color: red;
}
</style>
