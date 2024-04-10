<template>
  <div id="app">
    <Singup_form />
  </div>
</template>

<script>
import Singup_form from './components/Singup_form.vue'
import {ref} from "vue";

export default {
  name: 'App',
  components: {
    Singup_form
  },

}
</script>

<style>
#app {
  background-color: #eee;
  margin: 0px;
}
</style>
