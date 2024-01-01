<template>
	<div id="app">
		<Header />
		<Footer />
	</div>
</template>

<script>
export default Vue.defineComponent({
	name: "App",
	components: {
		Header: Vue.defineAsyncComponent(() =>
			loadModule("src/components/Header.vue", options),
		),
		Footer: Vue.defineAsyncComponent(() =>
			loadModule("src/components/Footer.vue", options),
		),
	},
	data() {
		return {
			data: {},
			playlists: [],
		}
	},
	mounted() {
		this.ImportData()
	},
	methods: {
		ImportData() {
			fetch("/src/data/data.json")
				.then((res) => res.json())
				.then((res) => {
					this.data = res
				})

			fetch("/src/data/playlists.csv")
				.then((res) => res.text())
				.then((res) => {
					this.playlists = res.split("\n").map((row) => row.split(","))
				})
		},
	},
})
</script>
