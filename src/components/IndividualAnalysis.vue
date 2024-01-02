<template>
	<div class="IndividualAnalysis">
		<h3>{{ target }}</h3>
		<details>
			<summary>TFIDF (keywords)</summary>

			<h4>Against global population</h4>

			<details>
				<summary>Counting</summary>
				<TfidfViewer :dataframe="dataThis['tfidf_counter_global']" />
			</details>

			<details>
				<summary>sum</summary>
				<TfidfViewer :dataframe="dataThis['tfidf_summer_global']" />
			</details>

			<h4>Against KPOP population</h4>

			<details>
				<summary>Counting</summary>
				<TfidfViewer :dataframe="dataThis['tfidf_counter_kpop']" />
			</details>

			<details>
				<summary>sum</summary>
				<TfidfViewer :dataframe="dataThis['tfidf_summer_kpop']" />
			</details>
		</details>

		<details>
			<summary>LDA (topic)</summary>

			<h4>Against global population</h4>

			<details>
				<summary>topics</summary>
				<LdaTopicViewer :htmlText="dataThis['lda_html_global']" />
			</details>

			<details>
				<summary>Counting</summary>
				<LdaViewer :dataframe="dataThis['lda_counter_global']" />
			</details>

			<details>
				<summary>sum</summary>
				<LdaViewer :dataframe="dataThis['lda_summer_global']" />
			</details>

			<h4>Against KPOP population</h4>

			<details>
				<summary>topics</summary>
				<LdaTopicViewer :htmlText="dataThis['lda_html_kpop']" />
			</details>

			<details>
				<summary>Counting</summary>
				<LdaViewer :dataframe="dataThis['lda_counter_kpop']" />
			</details>

			<details>
				<summary>sum</summary>
				<LdaViewer :dataframe="dataThis['lda_summer_kpop']" />
			</details>
		</details>

		<details>
			<summary>NRC Emotion Score</summary>

			<details>
				<summary>Noramlized mean emotion score</summary>
				<EmotionTable :vector="dataThis['normalized_mean_emotion_target']" />
			</details>

			<details>
				<summary>Ratio against global population (%)</summary>
				<EmotionTable :vector="dataThis['emotion_percentage_global']" />
			</details>

			<details>
				<summary>Ratio against KPOP population (%)</summary>
				<EmotionTable :vector="dataThis['emotion_percentage_kpop']" />
			</details>
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
		LdaTopicViewer: Vue.defineAsyncComponent(() =>
			loadModule("src/components/LdaTopicViewer.vue", options),
		),
		LdaViewer: Vue.defineAsyncComponent(() =>
			loadModule("src/components/LdaViewer.vue", options),
		),
		EmotionTable: Vue.defineAsyncComponent(() =>
			loadModule("src/components/EmotionTable.vue", options),
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
