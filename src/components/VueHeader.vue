<template>
	<div id="fondo-header">
		<img id="header-movil" src="images/bg-header-mobile.svg" alt="">
		<img id="header-escritorio" src="images/bg-header-desktop.svg" alt="">
	</div>
</template>

<script>
export default {

}
</script>

<style lang="sass" scoped>
	$verdeOscuro: #5DA5A4

	$breakpointMovil: 375px
	$breakpointEscritorio: 1440px

	#fondo-header
		background-color: $verdeOscuro
		max-height: 140px
		overflow: hidden

	#fondo-header img
		transform: scale(1.2)

	#header-movil
		width: 100%

	#header-escritorio
		width: 100%

	@media screen and (max-width: $breakpointEscritorio)
		#header-escritorio
			display: none

	@media screen and (min-width: $breakpointEscritorio)
		#header-movil
			display: none


</style>
