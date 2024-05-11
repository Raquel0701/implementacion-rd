<template>

  <Ejemplo />
  <div style="align-content: center;">

    <FormRegistro />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Ejemplo from './components/Ejemplo.vue'
import FormRegistro from './components/FormRegistro.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    Ejemplo,
    FormRegistro
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
