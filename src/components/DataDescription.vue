<template>
	<div id="DataDescription">
		<h2>Data Description</h2>

		<h3>Numbers of each groups</h3>
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

		<h3>Used playlists</h3>
		<details>
			<summary>Click to show</summary>
			<table>
				<tr>
					<th>playlist</th>
					<th>grouping name</th>
				</tr>
				<tr v-for="playlist in _playlists" :key="playlist[0]">
					<td>{{ playlist[0] }}</td>
					<td>{{ playlist[1] }}</td>
				</tr>
			</table>
		</details>
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
		totalMusic() {
			if (this.data == undefined) {
				return 0
			} else {
				return this.data["tracks_total"]
			}
		},

		_playlists() {
			if (this.playlists == undefined) return []

			let output = []
			for (let i = 1; i < this.playlists.length; i++) {
				output.push([this.playlists[i][0], this.playlists[i][1]])
			}

			return output
		},
	},
}
</script>
