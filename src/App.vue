<template>
  <div id="app">
		<vue-header></vue-header>
		<div class="container">
			<filtros
				:filtros_totales="filtros_totales"
				:filtrosSeleccionados="filtrosSeleccionados"
				@filtrosSeleccionados="filtrarOfertas"
				@filtroEliminado="eliminarFiltro"
			></filtros>
			<oferta-laboral
				v-for="(oferta, index) in ofertasLaboralesFiltradas" :key="index"
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
		<vue-footer></vue-footer>
  </div>
</template>

<script>
import jsonOfertasLaborales from './assets/data.json';
import OfertaLaboral from './components/OfertaLaboral';
import VueHeader from './components/VueHeader.vue';
import Filtros from './components/Filtros.vue';
import VueFooter from './components/VueFooter.vue';

export default {
  name: 'App',
  components: {
    OfertaLaboral,
		VueHeader,
		Filtros,
		VueFooter
  },
  data() {
    return {
      ofertasLaborales: jsonOfertasLaborales,
			ofertasLaboralesFiltradas: [],
			filtros_totales: [],
			filtrosSeleccionados: []
    }
  },
	mounted() {
		this.ofertasLaboralesFiltradas = this.ofertasLaborales;
		this.obtenerFiltros();
	},
	methods: {
		obtenerFiltros() {
			let filtros = [];

			for (let i = 0; i < jsonOfertasLaborales.length; i++) {
				const languages = jsonOfertasLaborales[i].languages;
				const tools = jsonOfertasLaborales[i].tools;
				const level = jsonOfertasLaborales[i].level;
				const role = jsonOfertasLaborales[i].role;

				languages.forEach(e => {
					if (!filtros.includes(e)) {
						filtros.push(e);
					}
				});

				tools.forEach(e => {
					if (!filtros.includes(e)) {
						filtros.push(e);
					}
				});

				if (!filtros.includes(level)) {
					filtros.push(level)
				}

				if (!filtros.includes(role)) {
					filtros.push(role)
				}
			}

			this.filtros_totales = filtros;
		},
		filtrarOfertas(filtros) {
			let ofertasFiltradas = this.ofertasLaborales.filter(oferta => {
				return filtros.every(i => oferta.languages.includes(i) || oferta.tools.includes(i) || oferta.level.includes(i) || oferta.role.includes(i));
			});

			this.ofertasLaboralesFiltradas = ofertasFiltradas;
			this.filtrosSeleccionados = filtros;
		},
		eliminarFiltro(filtroAEliminar) {
			let index = this.filtrosSeleccionados.indexOf(filtroAEliminar);
			this.filtrosSeleccionados.splice(index, 1);
			this.filtrarOfertas(this.filtrosSeleccionados);
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
