<template>
  <SignatureBuilder/>
</template>

<script>
import SignatureBuilder from './components/SignatureBuilder.vue'

export default {
  name: 'App',
  components: {
    SignatureBuilder
  }
}
</script>

<style>
  html {
    box-sizing: border-box;
  }

  *, *:before, *:after {
    box-sizing: inherit;
  }

  body {
    margin: 0;
    padding: 0;
    background: #F5F5F5;
    border-top: 5px solid #D30013;
  }
</style>
