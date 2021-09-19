<template>
	<div>
		<div class="filtros-wrapper" style="display: flex; flex-wrap: wrap;">
			<div v-for="(filtroSeleccionado, index) in filtrosSeleccionados" :key="index" class="filtroSeleccionado">
				<div class="nombre-filtro">
					{{filtroSeleccionado}}
				</div>
				<div class="boton-eliminar" @click="eliminarFiltro(filtroSeleccionado)">X</div>
			</div>
		</div>
		<input type="text" class="input-busqueda" :class="{'input-busqueda-vacio': busquedaInput.length == 0, 'input-busqueda-lleno': busquedaInput.length != 0}" v-model="busquedaInput" @input="escribiendoFiltro()" placeholder="Escribe una categoría...">
		<div class="resultados-wrapper" v-if="busquedaInput.length > 0">
			<div v-if="filtrosEncontrados.length > 0">
				<div v-for="(filtro, index) in this.filtrosEncontrados" :key="index" class="resultados-filtros" @click="seleccionarFiltro(filtro)">
					<p>{{filtro}}</p>
				</div>
			</div>
			<div v-else class="sin-resultados">
				<span>No se encontraron resultados</span>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		filtros_totales: [],
		filtrosSeleccionados: []
	},
	data() {
		return {
			busquedaInput: '',
			filtrosEncontrados: []
		}
	},
	methods: {
		escribiendoFiltro() {
			this.filtrosEncontrados = this.filtros_totales.filter(f =>
			f.toUpperCase().indexOf(this.busquedaInput.toUpperCase()) > -1
			&& this.filtrosSeleccionados.indexOf(f) == -1
			);
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
		},
		eliminarFiltro(filtroAEliminar) {
			this.$emit('filtroEliminado', filtroAEliminar);
		}
	}
}
</script>

<style lang="sass" scoped>
	@import url('https://fonts.googleapis.com/css2?family=Spartan:wght@100;200;300;400;500;600;700;800;900&display=swap')
	*
		font-family: 'Spartan', 'Arial', sans-serif
	$colorPrimario: #5DA5A4
	$colorPrimarioHover: #498281

	.input-busqueda
		width: 100%
		padding: 10px 12px
		border: 3px solid $colorPrimario
		outline: none

	.input-busqueda-vacio
		border-radius: 10px

	.input-busqueda-lleno
		border-radius: 10px 10px 0px 0px

	.resultados-wrapper
		background-color: #ffffff
		z-index: 1
		width: 100%
		border-right: 3px solid $colorPrimario
		border-bottom: 3px solid $colorPrimario
		border-left: 3px solid $colorPrimario
		border-radius: 0px 0px 10px 10px

	.resultados-filtros
		position: realtive
		padding: 10px 8px

	.resultados-filtros:hover
		background-color: $colorPrimario
		color: #ffffff
		cursor: pointer

	.filtros-wrapper
		margin-bottom: 14px

	.sin-resultados
		padding: 10px 8px
		color: #525252
		-webkit-touch-callout: none
		-webkit-user-select: none
		-khtml-user-select: none
		-moz-user-select: none
		-ms-user-select: none
		user-select: none

	.filtroSeleccionado
		display: flex
		align-items: center
		background-color: #ffffff
		color: $colorPrimario
		border-radius: 4px
		font-weight: 700
		overflow: hidden
		margin-right: 20px
		margin-bottom: 16px

	.nombre-filtro
		padding: 0px 10px

	.boton-eliminar
		display: flex
		align-items: center
		color: #ffffff
		background-color: $colorPrimario
		border: none
		padding: 3px 14px
		cursor: pointer
		font-size: 16px
		line-height: 32px
		font-weight: 700

	.boton-eliminar:hover
		background-color: $colorPrimarioHover

</style>
