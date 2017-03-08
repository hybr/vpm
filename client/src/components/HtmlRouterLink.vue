
<template>
	<router-link 
		v-if="inputField.html_tag === 'router-link'" 
		v-bind:to="inputField.link_to"
		:id="inputField.name + 'id'"
	>{{inputField.label}}</router-link>
</template>

<script>
	export default {
		name: 'html-router-link',
		props: ['inputField']
	}
</script>
