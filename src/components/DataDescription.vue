<template>
	<div id="DataDescription">
		<h2>Data Description</h2>

		<h3>numbers of each groups</h3>
		<table>
			<tr>
				<th>group</th>
				<th>number of musics</th>
			</tr>
			<tr v-for="group in groups" :key="group">
				<td>{{ group }}</td>
				<td>{{ GetMusicCount(group) }}</td>
			</tr>
		</table>
	</div>
</template>

<script>
export default {
	name: "DataDescription",
	props: {
		data: Object,
		playlists: Array,
		groups: Array,
	},
	methods: {
		GetMusicCount(group) {
			if (this.data == undefined) return 0

			return this.data["tracks_" + group]
		},
	},
	computed: {
		total_music() {
			if (this.data == undefined) {
				return 0
			} else {
				return this.data["tracks_total"]
			}
		},
	},
}
</script>
