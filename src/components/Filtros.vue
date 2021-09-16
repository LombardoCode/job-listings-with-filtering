<template>
	<div>
		<h1>Filtros</h1>
		<div v-for="(filtro, index) in filtros" :key="index">
			<span>{{filtro}}</span>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		filtros: []
	}
}
</script>

<style>

</style>
