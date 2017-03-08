<template>
	<single-form v-bind:single-form-info="formInfo" >Loading Form...</single-form>s
</template>

<script>
import auth from '../auth'
import SingleForm from './SingleForm.vue';

export default {

  data() {
    return {
            formInfo: {
                title: 'Join Us',
                summary: 'User Signup Form',
                redirec_message: '',
                actionMethod: "signup()",
                fields: [
                	{
                		name: '_1',
                		label: 'User Name',
                		html_tag: 'input',
                		type: 'text',
                		default_value: '',
                		data_clear_button: true,
                		placeholder: 'Please enter your user name',
                		v_model: 'credentials.username',
                		validations:   {
                			required: true
                		},
                		post: true
                	},
                	{
                		name: '_2',
                		label: 'User Password',
                		html_tag: 'input',
                		type: 'password',
                		default_value: '',
                		data_clear_button: true,
                		placeholder: 'Please enter your user password',
                		v_model: 'credentials.password',
                		validations:   {
                			required: true
                		},
                		post: true
                	},
                	{
                		name: '_5',
                		label: 'Confirm User Password',
                		html_tag: 'input',
                		type: 'password',
                		default_value: '',
                		data_clear_button: true,
                		placeholder: 'Please enter your user password',
                		v_model: 'credentials.confirm_password',
                		validations:   {
                			required: true
                		},
                		post: false
                	},
                	{
                		name: '_6',
                		label: 'User Name',
                		html_tag: 'input',
                		type: 'text',
                		default_value: '',
                		data_clear_button: true,
                		placeholder: 'Please enter your full name',
                		v_model: 'credentials.name',
                		validations:   {
                			required: false
                		},
                		post: true
                	},
                	{
                		name: '_3',
                		html_tag: 'button_set',
                		legend: '',
                		fields : [
		                	{
		                		name: '_1',
		                		label: 'Reset',
		                		html_tag: 'button',
		                		type: 'reset'	               		
		                	},
		                	{
		                		name: '_2',
		                		label: 'Submit',
		                		html_tag: 'button',
		                		type: 'submit'	               		
		                	},
		                	{
		                		name: '_3',
		                		label: 'Cancel',
		                		html_tag: 'button',
		                		type: 'button'	               		
		                	}
                		],
                		post: false
                	},
                	{
                		name: '_4',
                		label: 'Already Registered',
                		html_tag: 'router-link',
                		link_to: 'login',
                		post: false
                	}
                ]
            },
      credentials: {
        name: '',
        username: '',
        password: ''
      },
      errors: Object.assign({}, this.credentials)
    }
  },

  methods: {
    signup() {
      auth.signup(this, {user: this.credentials}, '/')
    }
  },
  	components: {
		'single-form' : SingleForm
	}
}
</script>
