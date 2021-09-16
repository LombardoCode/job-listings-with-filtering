<template>
  <div id="app">
		<vue-header></vue-header>
		<div class="container">
			<filtros :filtros="categoriasFiltradas"></filtros>
			<oferta-laboral
				v-for="(oferta, index) in ofertasLaborales" :key="index"
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
				@transferirCategoria="administrarCategorias"
			></oferta-laboral>
		</div>
    <div class="attribution">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>.
      Coded by <a href="#">Your Name Here</a>.
    </div>
  </div>
</template>

<script>
import jsonOfertasLaborales from './assets/data.json'
import OfertaLaboral from './components/OfertaLaboral'
import VueHeader from './components/VueHeader.vue'
import Filtros from './components/Filtros.vue';

export default {
  name: 'App',
  components: {
    OfertaLaboral,
		VueHeader,
		Filtros
  },
  data() {
    return {
      ofertasLaborales: jsonOfertasLaborales,
			categoriasFiltradas: []
    }
  },
	methods: {
		administrarCategorias(categoria) {
			if (!this.categoriasFiltradas.includes(categoria)) {
				this.categoriasFiltradas.push(categoria);
			}
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
