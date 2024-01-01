<template>
	<div v-html="htmlText"></div>
</template>

<script>
export default {
	name: "LdaTopicViewer",
	props: {
		htmlText: String,
	},
	watch: {
		htmlText() {},
	},
}
</script>
