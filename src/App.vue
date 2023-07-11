<script>
import HelloWorld from './components/HelloWorld.vue'
import { store } from './store.js';
import axios from 'axios';

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data() {
    return {
      store,
      name: "leonardocx",
      email: "santo@leoleo",
      password: "leonardo",
      token: localStorage['token'],
    }
  },
  created() {
    
  },
  methods: {
    getImagePath: function (imgPath) {
      return new URL(imgPath, import.meta.url).href;
    },
    login() {
      if (!localStorage['token']) {

        axios.post('http://127.0.0.1:8000/api/auth/login', {
          name: this.name,
          email: this.email,
          password: this.password
        }).then(res=>(
          console.log(res.data.message),
          localStorage['token'] = res.data.token,
          this.token = localStorage['token']
        ))
      } else {
        console.log("gia loggato")
      }

      },
      logout(){
        localStorage['token'] = '',
        this.token = ''
      }
  }
}
</script>

<template>
    <input  v-model="this.name" type="text" name="" id="">
    <input v-model="this.email" type="text" name="" id="">
    <input v-model="this.password" type="text" name="" id="">
    <input @click="login()" type="button" value="login">
    <input @click="logout()" type="button" value="logout">
    <p v-if="(this.token)">your token is: {{this.token}}</p>

</template>

<style lang="scss">
@use 'style/main.scss' as *;
</style>
