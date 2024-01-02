<template>
	<div :id="componentID" v-html="htmlText"></div>
</template>

<script>
export default {
	name: "LdaTopicViewer",
	props: {
		htmlText: String,
	},
	data() {
		return {
			componentID: MakeID(6),
		}
	},
	mounted() {
		this.RunScript()
	},
	methods: {
		RunScript() {
			const component = document.getElementById(this.componentID)
			const scripts = component.getElementsByTagName("script")
			for (let i = 0; i < scripts.length; i++) {
				const script = document.createElement("script")
				script.textContent = scripts[i].textContent
				document.body.appendChild(script)
			}
		},
	},
}
</script>
