
<template>
	<div class="ui-field-contain">
		<label :for="inputField.name + 'id'">{{inputField.label}}</label>
		<input v-if="inputField.html_tag === 'input'" 
			:id="inputField.name + 'id'"
			:type="inputField.type"
			:name="inputField.name"
			:value="inputField.default_value"
			:data-clear-btn="inputField.data_clear_button"
			:placeholder="inputField.placeholder"
			:v-model="inputField.v_model"
		/>
		<div class="ui-field-contain">

</div>
		<fieldset data-role="controlgroup" data-type="horizontal"
			v-if="inputField.html_tag === 'fieldset'"
			class="ui-grid-b ui-responsive">
				<legend>Horizontal controlgroup, buttons:</legend>

                                <button v-for="subField in inputField.fields" type="subField.type" class="ui-btn ui-corner-all ui-btn-a">{{subField.label}}</button>
			</fieldset>
		<router-link 
			v-if="inputField.html_tag === 'router-link'" 
			v-bind:to="inputField.link_to"
		>{{inputField.label}}</router-link>
	</div>
</template>

<script>
	import Vue from 'vue'
	export default {
		name: 'form-field',
		props: ['inputField']
	}
</script>

<style scoped>
.error-message {
  margin-top: 15px;
  margin-bottom: 30px;
  font-size: 15px;
  color: rgba(190, 64, 62, 0.65);
}
</style>
