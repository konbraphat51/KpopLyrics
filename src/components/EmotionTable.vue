<template>
	<table class="EmotionTable">
		<tr>
			<td>Emotion</td>
			<td>Score</td>
		</tr>
		<tr v-for="emotion in emotionList" :key="emotion">
			<td>{{ emotion }}</td>
			<td>{{ dataThis[emotion] }}</td>
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
			emotionList: [
				"anger",
				"anticipation",
				"disgust",
				"fear",
				"joy",
				"negative",
				"positive",
				"sadness",
				"surprise",
				"trust",
			],
		}
	},
	computed: {
		dataThis() {
			if (this.vector == undefined) return []

			let output = {}
			for (let i = 0; i < this.emotionList.length; i++) {
				let rounded = this.vector[i].toFixed(3)
				output[this.emotionList[i]] = rounded
			}

			return output
		},
	},
}
</script>

<style>
#EmotionTable table {
	border-collapse: collapse;
}
</style>
