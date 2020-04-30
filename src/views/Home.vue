<template>
  <div class="home">
    <div class="form-container" v-show="showForm">
      <h1>Join the Web Developers Club!</h1>
      <p>Sign up to access our special, secret page. Just create an account and answer a brief survey.</p>
      <p class="error-message" v-show="showError"> {{ errorMessage }} </p>
      <form v-on:submit.prevent="validateForm">
        <label>Username <input type="text" name="username" v-model="username" tabindex="0"></label>
        <label>Email <input type="text" name="email" v-model="email" tabindex="0"></label>
        <label>Password <input type="new-password" name="password" v-model="password" tabindex="0"></label>
        <label>Re-enter Password <input type="new-password" name="passwordVerify" v-model="passwordVerify" tabindex="0"></label>

        <p><input type="submit" value="Submit"></p>
      </form>
    </div>
    <div class="success-message" v-show="!showForm">
      <h1>Thank you for signing up!</h1>
      <p>Please take our new member survey.  <router-link to="/Survey">Click here</router-link></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      username: '',
      email: '',
      password: '',
      passwordVerify: '',
      showForm: true,
      showError: false,
      errorMessage: ''
    }
  },
  methods: {
    validateForm: function () {
      this.errorMessage = ''
      if (this.username === '') {
        this.errorMessage = this.errorMessage + 'Please enter a Username. '
      }
      if (this.email === '') {
        this.errorMessage = this.errorMessage + 'Please enter an Email. '
      } else if (!this.email.includes('@')) {
        this.errorMessage += 'Please format email address correctly. '
      }

      if (this.password === '') {
        this.errorMessage = this.errorMessage + 'Please enter a Password. '
      }
      if (this.password !== this.passwordVerify) {
        this.errorMessage = this.errorMessage + 'Passwords must match each other.'
      }
      if (this.errorMessage !== '') {
        this.showError = true
        this.showForm = true
      } else {
        this.showError = false
        this.showForm = false
      }
      return this.errorMessage
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  border: 1px solid #aa0000;
  padding: 1rem;
  color: #aa0000;
}
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
