<template>
	<div class="attribution container centrar-texto">
		Challenge by <a href="https://www.frontendmentor.io/challenges/job-listings-with-filtering-ivstIPCt" target="_blank">Frontend Mentor</a>.
		Coded by <a href="https://github.com/LombardoCode/">Lombardo Moreno Rodríguez</a>.
	</div>
</template>

<script>
export default {

}
</script>

<style lang="sass" scoped>
	@import url('https://fonts.googleapis.com/css2?family=Spartan:wght@100;200;300;400;500;600;700;800;900&display=swap')
	*
		font-family: 'Spartan', 'Arial', sans-serif

	.centrar-texto
		text-align: center

	.container
		width: 100%
		padding: 22px 20px

	@media screen and (min-width: 640px)
		.container
			max-width: 640px
			margin: 0 auto

	@media screen and (min-width: 768px)
		.container
			max-width: 768px
			margin: 0 auto

	@media screen and (min-width: 1024px)
		.container
			max-width: 1024px
			margin: 0 auto

	@media screen and (min-width: 1280px)
		.container
			max-width: 1280px
			margin: 0 auto

	@media screen and (min-width: 1536px)
		.container
			max-width: 1536px
			margin: 0 auto
</style>
