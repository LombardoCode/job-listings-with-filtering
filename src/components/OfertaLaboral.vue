<template>
  <div class="card flex-responsivo" :class="{'featured': featured}" style="">
		<div style="position: relative; display: flex;">
			<div class="posicion-imagen">
				<img :src="logo">
			</div>
			<div>
				<div class="margin-abajo" style="display: flex; align-items: center;">
					<span class="colorPrimario semibold separacion-derecha">{{company}}</span>
					<span v-if="new_offer" class="etiqueta bgPrimario bold separacion-derecha font-sm">new!</span>
					<span v-if="featured" class="etiqueta bgSecundario bold font-sm">featured</span>
				</div>
				<div>
					<h3 class="titular-puesto margin-abajo">{{position}}</h3>
					<ul class="flex margin-abajo">
						<li class="flex-item">{{postedAt}}</li>
						<li class="flex-item">{{contract}}</li>
						<li class="flex-item">{{location}}</li>
					</ul>
				</div>
			</div>
		</div>
		<hr class="margin-hr">
		<div style="display: flex; flex-wrap: wrap;">
			<span class="colorPrimario semibold separacion-tags">{{role}}</span>
			<span class="colorPrimario semibold separacion-tags">{{level}}</span>
			<span v-for="(tool, index) in tools" :key="index" class="colorPrimario semibold separacion-tags">{{tool}}</span>
			<span v-for="(language, index) in languages" :key="index" class="colorPrimario semibold separacion-tags">{{language}}</span>
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

<style lang="sass" scoped>
	@import url('https://fonts.googleapis.com/css2?family=Spartan:wght@100;200;300;400;500;600;700;800;900&display=swap')
	*
		font-family: 'Spartan', 'Arial', sans-serif

	$LightGrayishCyanBackground: hsl(180, 52%, 96%)
	$LightGrayishCyanTablets: hsl(180, 31%, 95%)
	$DarkGrayishCyan: hsl(180, 8%, 52%)
	$VeryDarkGrayishCyan: hsl(180, 14%, 20%)
	$colorPrimario: #31a2a3
	$colorSecundario: #113436
	$sombraCard: rgba(41, 134, 135, 0.26)

	$breakpointMovil: 375px
	$breakpointEscritorio: 1440px

	.colorPrimario
		color: $colorPrimario

	.texto-blanco
		color: #ffffff

	.bgPrimario
		background-color: $colorPrimario

	.bgSecundario
		background-color: $colorSecundario

	.semibold
		font-weight: 700

	.bold
		font-weight: 800

	.flex-responsivo
		display: flex
		justify-content: space-between
		align-items: center

	@media screen and (min-width: $breakpointEscritorio)
		.flex-responsivo
			display: flex
			justify-content: space-between
			align-items: center

	.card
		background-color: #ffffff
		padding: 44px 18px 44px 24px
		margin-top: 60px
		border-radius: 6px
		box-shadow: 0px 10px 19px 0px $sombraCard

	@media screen and (max-width: $breakpointEscritorio)
		.card
			display: block
			margin-top: 80px
			padding: 44px 18px 0px 24px

	.posicion-imagen
		position: absolute
		width: 70px
		bottom: 110px

	@media screen and (min-width: $breakpointEscritorio)
		.posicion-imagen
			position: static
			padding-right: 110px

	.featured
		border-left: 8px solid $colorPrimario

	.etiqueta
		text-transform: uppercase
		padding: 0px 10px
		color: #ffffff
		border-radius: 9999px
		line-height: 30px

	.margin-abajo
		margin-bottom: 12px

	.padding-abajo
		padding-bottom: 12px

	.separacion-derecha
		margin-right: 10px

	.flex
		display: flex

	.flex::child(1)
		color: red

	.flex-item
		margin-right: 32px

	.font-sm
		font-size: 13px

	li
		color: #696969

	li:nth-child(1)
		list-style-type: none

	.titular-puesto
		color: #525252

	.margin-hr
		margin: 24px 0px
		background-color: #696969
		border: none
		height: 1px

	@media screen and (min-width: $breakpointEscritorio)
		.margin-hr
			display: none

	.separacion-tags
		margin-right: 16px
		margin-bottom: 28px

	@media screen and (min-width: $breakpointEscritorio)
		.separacion-tags
			margin-bottom: 0px
</style>
