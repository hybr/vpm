
<template>
    <fieldset 
		v-if="inputField.html_tag === 'button_set'"
		data-role="controlgroup" 
		data-type="horizontal"
		class="ui-field-contain"
	>
		<legend>{{inputField.legend}}</legend>
		<input
			v-for="subField in inputField.fields" 
			:type="subField.type"
			:id="inputField.name + subField.name + 'id'"
			:name="subField.label + 'name'"
			:value="subField.label"
		/>
    </fieldset>
</template>

<script>
	export default {
		name: 'form-field-button-set',
		props: ['inputField']
	}
</script>