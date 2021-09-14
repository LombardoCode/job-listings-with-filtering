<template>
	<div id="fondo-header">
		<img id="header-movil" src="/images/bg-header-mobile.svg" alt="">
		<img id="header-escritorio" src="/images/bg-header-desktop.svg" alt="">
	</div>
</template>

<script>
export default {

}
</script>

<style lang="sass" scoped>
	$LightGrayishCyanBackground: hsl(180, 52%, 96%)
	$LightGrayishCyanTablets: hsl(180, 31%, 95%)
	$DarkGrayishCyan: hsl(180, 8%, 52%)
	$VeryDarkGrayishCyan: hsl(180, 14%, 20%)
	#fondo-header
		background-color: $DarkGrayishCyan

	#header-movil
		width: 100%
</style>
