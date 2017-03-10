
<template>
	<span
		v-if="inputField.html_tag === 'input'"
		class="input-field"
	>
	   <i class="material-icons prefix">{{inputField.icon_name}}</i>
		<label 
			:for="inputField.name + 'id'"
		>{{inputField.label}}</label><br />
		<input 
			:id="inputField.name + 'id'"
			:type="inputField.type"
			:name="inputField.name + 'name'"
			:value="inputField.default_value"
			:data-clear-btn="inputField.data_clear_button"
			:placeholder="inputField.placeholder"
			:v-model="inputField.v_model"
		/>
	</span>
</template>

<script>
	export default {
		name: 'form-field-input',
		props: ['inputField']
	}
</script>
