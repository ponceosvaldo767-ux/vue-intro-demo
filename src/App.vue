<template>
  <div id="app">
    <MyComponent />
  </div>
</template>

<script>
import MyComponent from './components/MyComponet.vue'

export default {
  name: 'App',
  components: {
    MyComponent
  }
}
</script>

<style>
body {
  margin: 0;
  background-color: #f0f2f5;
}
</style>