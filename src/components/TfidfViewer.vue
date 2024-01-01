<template>
	<div :id="tableID"></div>
</template>

<script>
export default {
	name: "TfidfViwer",
	props: {
		dataframe: Object,
	},
	data() {
		return {
			tableID: MakeID(6),
		}
	},
	computed: {
		dataThis() {
			if (this.dataframe == undefined) return {}

			return this.dataframe
		},
	},
}
</script>
