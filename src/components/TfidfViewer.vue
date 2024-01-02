<template>
	<div :id="tableID"></div>
</template>

<script>
export default {
	name: "TfidfViwer",
	props: {
		dataframe: Array,
	},
	data() {
		return {
			tableID: MakeID(6),
			table: null,
		}
	},
	mounted() {
		this.MakeTable()
	},
	computed: {
		dataThis() {
			if (this.dataframe == undefined) return []

			let output = []

			this.dataframe.forEach((element) => {
				output.push({
					word: element[0],
					score: element[1],
				})
			})

			return output
		},
	},
	methods: {
		MakeTable() {
			this.table = new Tabulator("#" + this.tableID, {
				data: this.dataThis,
				layout: "fitColumns",
				pagination: "local",
				paginationSize: 10,
				columns: [
					{title: "word", field: "word"},
					{title: "score", field: "score"},
				],
			})
		},
	},
	watch: {
		dataframe() {
			this.MakeTable()
		},
	},
}
</script>
