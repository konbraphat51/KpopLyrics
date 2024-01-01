<template>
	<div class="IndividualAnalysis">
		<h3>{{ target }}</h3>
	</div>
</template>

<script>
export default {
	name: "IndividualAnalysis",
	props: {
		target: String,
		data: Object,
	},
}
</script>
