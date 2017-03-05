<template>
	<label :for="field.name + 'id'">{{field.label}}</label>
	<input v-if="field.html_tag === 'input'" 
		:id="field.name + 'id'"
		:type="field.type"
		:name="field.name"
		:value="field.default_value"
		:data-clear-btn="field.data_clear_button"
		:placeholder="field.placeholder"
		:v-model="field.v_model"
	>
	<p class="error-message" v-if="errors.username">{{ errors.username }}</p>
</template>

<script>
export default {
    data() {
        return {
			field : {}
		}
	},
 	methods: {
	}
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
