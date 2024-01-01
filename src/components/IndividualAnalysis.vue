<template>
	<div class="IndividualAnalysis">
		<h3>{{ target }}</h3>
		<details>
			<summary>TFIDF (keywords)</summary>

			<details>
				<summary>What is TFIDF?</summary>
				<p>
					TFIDF indicates how important a word is to a document in a corpus.<br />
					<a
						href="https://medium.com/nlplanet/two-minutes-nlp-learn-tf-idf-with-easy-examples-7c15957b4cb3"
					>
						More information
					</a>
				</p>
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
