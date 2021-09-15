<template>
  <div id="app">
		<vue-header></vue-header>
		<div class="container">
			<oferta-laboral
				v-for="(oferta, index) in datosOfertasLaborales" :key="index"
				:id="oferta.id"
				:company="oferta.company"
				:logo="oferta.logo"
				:new_offer="oferta.new"
				:featured="oferta.featured"
				:position="oferta.position"
				:role="oferta.role"
				:level="oferta.level"
				:postedAt="oferta.postedAt"
				:contract="oferta.contract"
				:location="oferta.location"
				:languages="oferta.languages"
				:tools="oferta.tools"
			></oferta-laboral>
		</div>
    <div class="attribution">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>.
      Coded by <a href="#">Your Name Here</a>.
    </div>
  </div>
</template>

<script>
import datosOfertasLaborales from './assets/data.json'
import OfertaLaboral from './components/OfertaLaboral'
import VueHeader from './components/VueHeader.vue'
export default {
  name: 'App',
  components: {
    OfertaLaboral,
		VueHeader
  },
  data() {
    return {
      datosOfertasLaborales
    }
  }
}
</script>

<style lang="sass">
	html
		box-sizing: border-box
		margin: 0
		padding: 0

	*, *:before, *:after
		box-sizing: inherit
		margin: 0
		padding: 0

	.container
		padding: 22px 20px
</style>
