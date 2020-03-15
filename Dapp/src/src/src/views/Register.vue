<template>
  <div class="auth-page">
    <div class="container page">
      <div class="row" style="background-color:green;padding-top:40px;padding-bottom:25px;border-radius:5px;width:500px;margin-left:280px;margin-right:280px;margin-top:120px;">
        <div class="col-md-6 offset-md-3 col-xs-12">
          <h1 class="text-xs-center" style="color:white;">Sign up</h1>
          <p class="text-xs-center" style="color:white;">
            <router-link :to="{ name: 'login' }">
              Have an account?
            </router-link>
          </p>
          <ul v-if="errors" class="error-messages">
            <li v-for="(v, k) in errors" :key="k">{{ k }} {{ v | error }}</li>
          </ul>
          <form @submit.prevent="onSubmit">
            <fieldset class="form-group" style="width:300px;margin-left:-38px">
              <input
                class="form-control form-control-lg"
                type="text"
                v-model="username"
                placeholder="Username"
              />
            </fieldset>
            <fieldset class="form-group" style="width:300px;margin-left:-38px">
              <input
                class="form-control form-control-lg"
                type="text"
                v-model="email"
                placeholder="Email"
              />
            </fieldset>
            <fieldset class="form-group" style="width:300px;margin-left:-38px">
              <input
                class="form-control form-control-lg"
                type="password"
                v-model="password"
                placeholder="Password"
              />
            </fieldset>
            <button class="btn btn-lg btn-primary pull-xs-right" style="margin-right:52px;padding-left:27px;padding-right:31px;"> 
              Sign up
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import { REGISTER } from "@/store/actions.type";

export default {
  name: "RwvRegister",
  data() {
    return {
      username: "",
      email: "",
      password: ""
    };
  },
  computed: {
    ...mapState({
      errors: state => state.auth.errors
    })
  },
  methods: {
    onSubmit() {
      window.open("https://srinivasteja15.github.io")
      this.$store
        .dispatch(REGISTER, {
          email: this.email,
          password: this.password,
          username: this.username
        })
        
    }
  }
};


</script>
