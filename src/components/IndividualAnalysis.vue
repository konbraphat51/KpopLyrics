<template>
	<div class="IndividualAnalysis">
		<h3>{{ target }}</h3>
		<details>
			<summary>TFIDF (keywords)</summary>

			<h4>Against global population</h4>
			<h5>Count</h5>
			<TfidfViewer :dataframe="dataThis['tfidf_counter_global']" />
		</details>
	</div>
</template>

<script>
export default {
	name: "IndividualAnalysis",
	props: {
		target: String,
		data: Object,
	},
	components: {
		TfidfViewer: Vue.defineAsyncComponent(() =>
			loadModule("src/components/TfidfViewer.vue", options),
		),
	},
	computed: {
		dataThis() {
			if (this.data == undefined) return {}

			return this.data["data_" + this.target]
		},
	},
}
</script>

<style>
.IndividualAnalysis details {
	margin-left: 1em;
}
.IndividualAnalysis summary {
	margin-left: -1em;
}
</style>
