<template>
    <single-form v-bind:single-form-info="formInfo" >Loading Form...</single-form>
</template>

<script>
import auth from '../auth'
import SingleForm from './SingleForm.vue';

export default {
    data() {
        return {
            formInfo: {
                title: 'Login',
                summary: 'User Login Form',
                redirec_message: 'You need to login first',
                actionMethod: "login",
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
                		]
                	},
                	{
                		name: '_4',
                		label: 'Forget Password',
                		html_tag: 'router-link',
                		link_to: 'forget_password'                		
                	},
                	{
                		name: '_5',
                		label: 'Need An Account',
                		html_tag: 'router-link',
                		link_to: 'signup'                		
                	},
                ]
            },
            credentials: {
				username: '',
				password: '',
				name: ''
			},
			error: '',
			errors: Object.assign({}, this.credentials)
		}
  },
  methods: {
    login() {

      this._validateLoginForm()

      const credentials = {
        username: this.credentials.username,
        password: this.credentials.password
      }

      if(this.credentials.username && this.credentials.password){
        auth.login(this, {session: credentials}, '/')
        this.errors = { username: "", password: "" }
      }
    },

    _validateLoginForm() {

      this.error = ""

      if(!this.credentials.username && !this.credentials.password){
        this.errors = {
          username: "can't be blank",
          password: "can't be blank",
        }
        return
      }

      if(!this.credentials.username){
        this.errors = {
          username: "can't be blank",
          password: ""
        }
        return
      }

      if(!this.credentials.password){
        this.errors = {
          username: "",
          password: "can't be blank"
        }
        return
      }
    }
  },
  	components: {
		'single-form' : SingleForm
	}
}
</script>

<style scoped>
.redirect-message {
  margin-top: 0px;
  margin-bottom: 40px;
  font-size: 17px;
  color: #4caf50;
  font-weight: bold;
  text-transform: uppercase;
}
.error-message {
  margin-top: 15px;
  margin-bottom: 30px;
  font-size: 15px;
  color: rgba(190, 64, 62, 0.65);
}
</style>
