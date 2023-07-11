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
    }
  },
  created() {
    this.createLeo()
  },
  methods: {
    getImagePath: function (imgPath) {
      return new URL(imgPath, import.meta.url).href;
    },
    createLeo() {
      axios.post('http://127.0.0.1:8000/api/auth/login', {
        name: 'leonardocx1',
        email: 'santo1@leoleo',
        password: 'leonardo'
      }).then(res=>(console.log(res)))
    }
  }
}
</script>

<template>
  
</template>

<style lang="scss">
@use 'style/main.scss' as *;
</style>
