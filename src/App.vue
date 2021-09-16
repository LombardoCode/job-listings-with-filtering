<template>
  <div id="app">
		<vue-header></vue-header>
		<div class="container">
			<filtros :filtros="categorias"></filtros>
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
			categorias: []
    }
  },
	mounted() {
		this.obtenerCategorias();
	},
	methods: {
		administrarCategorias(categoria) {
			if (!this.categoriasFiltradas.includes(categoria)) {
				this.categoriasFiltradas.push(categoria);
			}
		},
		obtenerCategorias() {
			let categorias = [];

			for (let i = 0; i < jsonOfertasLaborales.length; i++) {
				const languages = jsonOfertasLaborales[i].languages;
				const tools = jsonOfertasLaborales[i].tools;
				const level = jsonOfertasLaborales[i].level;
				const role = jsonOfertasLaborales[i].role;

				languages.forEach(e => {
					if (!categorias.includes(e)) {
						categorias.push(e);
					}
				});

				tools.forEach(e => {
					if (!categorias.includes(e)) {
						categorias.push(e);
					}
				});

				if (!categorias.includes(level)) {
					categorias.push(level)
				}

				if (!categorias.includes(role)) {
					categorias.push(role)
				}
			}

			this.categorias = categorias;
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
