
<template>
    <section>
      <form @submit.prevent="singleFormInfo.actionMethod">
         <div class="row"><div class="col s12 m12 l12">
            <h3>{{ singleFormInfo.title }}</h3>
          </div></div>

        <div class="row"><div class="col s12 m12 l12">
          {{ singleFormInfo.summary }}
        </div></div>
        
        
        <div class="row"><div class="col s12 m12 l12">
          {{ singleFormInfo.redirec_message }}
        </div></div>

      <div v-for="field in singleFormInfo.fields">
      <div class="row" ><div class="col s12 m12 l12">
          <form-field-button-set
            v-if="field.html_tag === 'button_set'" 
            v-bind:input-field="field"
          >Loading Button Set Field...</form-field-button-set>
      </div></div>

      <div class="row"><div class="col s12 m12 l12">
          <form-field-input
          v-if="field.html_tag === 'input'" 
          v-bind:input-field="field"
        >Loading Input Field...</form-field-input>
      </div></div>

      <div class="row"><div class="col s12 m12 l12">
          <html-router-link 
          v-if="field.html_tag === 'router-link'" 
          v-bind:input-field="field"
         >Loading Router Link...</html-router-link>
      </div></div>
      
      </div>
      
      
      </form>
    </section>
</template>

<script>
	import FormFieldInput from './FormFieldInput.vue';
	import FormFieldButtonSet from './FormFieldButtonSet.vue';
	import HtmlRouterLink from './HtmlRouterLink.vue';
	
	export default {
		name: 'single-form',
		props: ['singleFormInfo'],
		components: {
			'html-router-link': HtmlRouterLink,
			'form-field-input': FormFieldInput,
			'form-field-button-set' : FormFieldButtonSet
		}
	}
</script>