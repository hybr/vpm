
<template>
	<form @submit.prevent="singleFormInfo.actionMethod">

            <div data-role="header">
                <h3>{{ singleFormInfo.title }}</h3>
            </div>
            <div data-role="main" class="ui-content ui-responsive">
                <p>{{ singleFormInfo.summary }}</p>
                <p v-if="$route.query.redirect">
                    {{ singleFormInfo.redirec_message }}
                </p>
                <ul data-role="listview" data-inset="true">
					<li v-for="field in singleFormInfo.fields">
						<form-field-button-set
							v-if="field.html_tag === 'button_set'" 
							v-bind:input-field="field"
						>Loading Button Set Field...</form-field-button-set>
						<form-field-input
							v-if="field.html_tag === 'input'" 
							v-bind:input-field="field"
						>Loading Input Field...</form-field-input>
						<html-router-link 
							v-if="field.html_tag === 'router-link'" 
							v-bind:input-field="field"
						>Loading Router Link...</html-router-link>
					</li>
                </ul>
            </div>

    </form>
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