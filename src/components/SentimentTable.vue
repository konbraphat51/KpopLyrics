<template>
	<table class="EmotionTable">
		<tr>
			<td>Sentiment</td>
			<td>Score</td>
		</tr>
		<tr v-for="sentiment in sentimentList" :key="sentiment">
			<td>{{ sentiment }}</td>
			<td>{{ dataThis[sentiment] }}</td>
		</tr>
	</table>
</template>

<script>
export default {
	name: "EmotionTable",
	props: {
		vector: Array,
	},
	data() {
		return {
			sentimentList: ["negative", "positive"],
		}
	},
	computed: {
		dataThis() {
			if (this.vector == undefined) return []

			let output = {}
			for (let i = 0; i < this.sentimentList.length; i++) {
				let rounded = this.vector[i].toFixed(3)
				output[this.sentimentList[i]] = rounded
			}

			return output
		},
	},
}
</script>

<style>
#EmotionTable {
	border-collapse: collapse;
}
</style>
