<template>
	<div>
		<input type="text" style="width: 100%; padding: 10px 4px" v-model="busquedaInput" @input="escribiendoCategoria()" placeholder="Escribe una categoría...">
		<div style="position: relative;">
			<div style="position: absolute; background-color: #ffffff; z-index: 1; width: 100%;">
				<div v-for="(filtro, index) in this.categoriasEncontradas" :key="index" class="">
					<p>{{filtro}}</p>
				</div>
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
			categoriasEncontradas: []
		}
	},
	methods: {
		escribiendoCategoria() {
			this.categoriasEncontradas = this.filtros.filter(f =>  f.toUpperCase().indexOf(this.busquedaInput.toUpperCase()) > -1 );
		}
	}
}
</script>

<style>

</style>
