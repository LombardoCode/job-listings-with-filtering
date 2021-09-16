<template>
	<div>
		<div id="filtros-seleccionados">
			<div v-for="(filtroSeleccionado, index) in filtrosSeleccionados" :key="index">
				<p>{{filtroSeleccionado}}</p>
			</div>
		</div>
		<input type="text" class="input-busqueda" v-model="busquedaInput" @input="escribiendoFiltro()" placeholder="Escribe una categoría...">
		<div class="resultados-wrapper" style="position: absolute; background-color: #ffffff; z-index: 1; width: 100%;">
			<div v-for="(filtro, index) in this.filtrosEncontrados" :key="index" class="resultados-filtros" @click="seleccionarFiltro(filtro)">
				<p>{{filtro}}</p>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		filtros: []
	},
	data() {
		return {
			busquedaInput: '',
			filtrosEncontrados: [],
			filtrosSeleccionados: []
		}
	},
	methods: {
		escribiendoFiltro() {
			this.filtrosEncontrados = this.filtros.filter(f =>  f.toUpperCase().indexOf(this.busquedaInput.toUpperCase()) > -1 );
		},
		seleccionarFiltro(filtro) {
			if (!this.filtrosSeleccionados.includes(filtro)) {
				this.filtrosSeleccionados.push(filtro);
				this.filtrarOfertas();
			}

			this.busquedaInput = '';
			this.filtrosEncontrados = [];
		},
		filtrarOfertas() {
			this.$emit('filtrosSeleccionados', this.filtrosSeleccionados);
		}
	}
}
</script>

<style lang="sass" scoped>
	@import url('https://fonts.googleapis.com/css2?family=Spartan:wght@100;200;300;400;500;600;700;800;900&display=swap')
	*
		font-family: 'Spartan', 'Arial', sans-serif
	$colorPrimario: #5DA5A4

	.input-busqueda
		width: 100%
		padding: 10px 12px
		border-radius: 10px
		border-width: 2px
		border-color: $colorPrimario

	.resultados-wrapper
		position: relative
		border-width: 2px
		border-color: $colorPrimario

	.resultados-filtros
		padding: 10px 8px

	.resultados-filtros:hover
		background-color: $colorPrimario
		color: #ffffff
		cursor: pointer
</style>
