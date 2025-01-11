<template>
	<div class="pilot-modal">
		<div class="pilot-header-container">
			<div class="section-header clipped-medium-backward-bio">
				<img src="/icons/pilot-icon.svg" />
				<h1>Carduelis-V</h1>
			</div>
			<div class="rhombus-back">&nbsp;</div>
		</div>
		<div class="pilot">
			<Markdown :source="bio" class="markdown" />
		</div>
	</div>
	<div class="pilot-modal portrait">
		<div class="pilot-header-container">
			<div class="section-header clipped-medium-backward-pilot">
				<img src="/icons/portrait-icon.svg" />
				<h1>Satellite Image</h1>
			</div>
			<div class="rhombus-back">&nbsp;</div>
		</div>
		<div class="pilot">
			<img :src="portrait" class="portrait" />
		</div>
	</div>
</template>

<script>
import Markdown from 'vue3-markdown-it';

export default {
	components: {
		Markdown
	},
	data() {
		return {
			bio: "",
		}
	},
	props: {
	},
	computed: {
		portrait() {
			return `/pilots/kal.png`
		},
	},
	created() {		
        let self = this;
        console.log("PlanetModal loaded");

		let md = `/planet/carduelis-v.md`;
		var client = new XMLHttpRequest();
		client.open('GET', md);

        console.log("response: ", client.responseText);

		client.onreadystatechange = function () {
			self.bio = client.responseText;
		}
		client.send();
	},
	methods: {

	}
}
</script>