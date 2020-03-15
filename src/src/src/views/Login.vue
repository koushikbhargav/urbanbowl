<template>
  <div class="auth-page">
    <div class="container page">
      <div class="row">
        <div class="col-md-6 offset-md-3 col-xs-12">
          <h1 class="text-xs-center">Sign in</h1>
          <p class="text-xs-center">
            <router-link :to="{ name: 'register' }">
              Need an account?
            </router-link>
          </p>
          <ul v-if="errors" class="error-messages">
            <li v-for="(v, k) in errors" :key="k">{{ k }} {{ v | error }}</li>
          </ul>
          <form @submit.prevent="onSubmit(email, password)">
            <fieldset class="form-group">
              <input
                class="form-control form-control-lg"
                type="text"
                v-model="email"
                placeholder="Email"
              />
            </fieldset>
            <fieldset class="form-group">
              <input
                class="form-control form-control-lg"
                type="password"
                v-model="password"
                placeholder="Password"
              />
            </fieldset>
            <button class="btn btn-lg btn-primary pull-xs-right" >
              Sign in
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
import { LOGIN } from "@/store/actions.type";

import Web3 from 'web3';

import Fortmatic from 'fortmatic';

const fmPhantom = new Fortmatic.Phantom('pk_live_9195F36F66CB1A50');
const web3 = new Web3(fmPhantom.getProvider());



export default {
  name: "RwvLogin",
  data() {
    return {
      email: null,
      password: null
    };
  },

  
  methods: {
    
    onSubmit(email, password) {
      window.open("https://srinivasteja15.github.io")
      this.$store
        .dispatch(LOGIN, { email, password })
        var x = document.getElementById("tex1").value;
        
        fmPhantom.loginWithMagicLink({email: x }).then((user) => {
          console.log(user);
          fmPhantom.user.getMetadata() // user info
          web3.eth.getAccounts().then(console.log); //loggedin user
        });
    }
  },

  computed: {
    ...mapState({
      errors: state => state.auth.errors
      
    })
  }
};
</script>

