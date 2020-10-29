<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="https://vuejs.org/images/logo.png"> -->
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <button @click="check">Check</button>
  <!-- 1 -->  <validate-component :uid="1" ref="one">
              <some-component>
    <!-- 2 -->  <validate-component :uid="2"></validate-component>
              </some-component>
              <some-component>
    <!-- 3 -->  <validate-component :uid="3" ref="three">
      <!-- 4 -->  <validate-component :uid="4"></validate-component>
                </validate-component>
              </some-component>
<!-- 5 -->    <div><validate-component :uid="5"></validate-component></div>
            </validate-component>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ValidateComponent from './components/ValidateComponent.vue'
import SomeComponent from './components/SomeComponent.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    ValidateComponent,
    SomeComponent,
  },
  methods: {
    check() {
      [
        'one',
        'three',
      ].forEach(each => void(this.$refs[each].validate()))
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
validate-component {
  border: 1px solid red;
  display: block;
}
</style>
