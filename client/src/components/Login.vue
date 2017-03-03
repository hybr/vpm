<template>
    <form @submit.prevent="login">
        <div data-inset="true">
            <div class="ui-bar ui-bar-a">
                <h3>{{ form.title }}</h3>
            </div>
            <div class="ui-body u-body-a">
                <p>{{ form.summary }}</p>
                <p v-if="$route.query.redirect">
                    {{ form.redirec_message }}
                </p>
                <ul data-role="listview" data-inset="true">
                    <li class="ui-field-contain">
                        <label for="name2">User Name</label>
                        <input 
                            type="text" 
                            name="name2" 
                            id="name2" 
                            value="" 
                            data-clear-btn="true" 
                            placeholder="Enter your username" 
                            v-model="credentials.username"
                        >
                        <p v-if="errors.username">{{ errors.username }}</p>
                    </li>
                    <li class="ui-field-contain">
                        <label for="password">Password</label>
                        <input 
                            type="password" 
                            name="password" 
                            id="name2" 
                            value="" 
                            data-clear-btn="true" 
                            placeholder="Enter your password" 
                            v-model="credentials.password">
                        <p v-if="errors.password">{{ errors.password }}</p>
                    </li>
                    <li class="ui-field-contain">
                        <fieldset  class="ui-grid-b ui-responsive">
                            <div class="ui-block-a">
                                <button type="reset" class="ui-btn ui-corner-all ui-btn-a">Reset</button>
                            </div>
                            <div class="ui-block-b">
                                <button type="submit" class="ui-btn ui-corner-all ui-btn-a">Cancel</button>
                            </div>
                            <div class="ui-block-c">
                                <button type="submit" class="ui-btn ui-corner-all ui-btn-a">Submit</button>
                            </div>
                            <p v-if="error">{{ error }}</p>
                        </fieldset>
                    </li>
                    <li>
                        <router-link to="forget_password">Forgot Password</router-link>
                    </li>
                    <li>
                        <router-link to="signup">Need An Account</router-link>
                    </li>
                </ul>
            </div>
        </div>
    </form>
</template>

<script>
import auth from '../auth'

export default {

    data() {
        return {
            form: {
                title: 'Login',
                summary: 'User Login Form',
                redirec_message: 'You need to login first'
            },
            credentials: {
        username: '',
        password: ''
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
