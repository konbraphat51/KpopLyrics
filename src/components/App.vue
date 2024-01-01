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
			data: [],
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
		},
	},
})
</script>
