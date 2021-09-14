<template>
  <div>
    <img :src="logo" alt="">
		<div>
			<span>{{company}}</span>
			<span v-if="new_offer">new!</span>
			<span v-if="featured">featured</span>
		</div>
		<div>
			<h3>{{position}}</h3>
			<div>
				<span>{{postedAt}}</span>
				<span>{{contract}}</span>
				<span>{{location}}</span>
			</div>
			<div>
				<span>{{role}}</span>
				<span>{{level}}</span>
				<span>{{location}}</span>
				<span>{{languages}}</span>
				<span>{{tools}}</span>
			</div>
		</div>
  </div>
</template>

<script>
export default {
	props: {
		id: Number,
		company: String,
		logo: String,
		new_offer: Boolean,
		featured: Boolean,
		position: String,
		role: String,
		level: String,
		postedAt: String,
		contract: String,
		location: String,
		languages: [],
		tools: [],
	}
}
</script>

<style>

</style>
