<template>
	<div id="app">
		<Header />
		<div id="loading" v-if="!(loadedData && loadedPlaylists)">Loading...</div>
		<MethodsDescription />
		<DataDescription :data="data" :playlists="playlists" :groups="groups" />
		<h2>IndividualAnalysis</h2>
		<IndividualAnalysis
			v-for="group in groups"
			:key="group"
			:target="group"
			:data="data"
		/>
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
		MethodsDescription: Vue.defineAsyncComponent(() =>
			loadModule("src/components/MethodsDescription.vue", options),
		),
		DataDescription: Vue.defineAsyncComponent(() =>
			loadModule("src/components/DataDescription.vue", options),
		),
		IndividualAnalysis: Vue.defineAsyncComponent(() =>
			loadModule("src/components/IndividualAnalysis.vue", options),
		),
	},
	data() {
		return {
			data: undefined,
			playlists: undefined,
			groups: ["kpop", "bts", "seventeen", "twice", "itzy"],
			loadedData: false,
			loadedPlaylists: false,
		}
	},
	mounted() {
		this.ImportData()
	},
	methods: {
		ImportData() {
			fetch("src/data/data.json")
				.then((res) => res.json())
				.then((res) => {
					this.data = res
					this.loadedData = true
				})

			fetch("src/data/playlists.csv")
				.then((res) => res.text())
				.then((res) => {
					this.playlists = res.split("\n").map((row) => row.split(","))
					this.loadedPlaylists = true
				})
		},
	},
})
</script>

<style>
#loading {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background-color: rgb(255, 200, 200);
	z-index: 100;
	display: flex;
	justify-content: center;
	align-items: center;
}

#app h2 {
	padding: 0.1rem 0rem;
	margin-bottom: 0.2rem;
	border-bottom: 1px solid #000000;
	font-weight: bold;
	font-size: 26px;
}

#app {
	font: 1rem sans-serif;
}
</style>
