<template>

  <Header />

  <div class="container">

    <router-view />

  </div>

</template>

<script>

  import Header from '@/components/Header'

  export default {

    components: {
      Header
    },

  }


</script>

<style>

  body {
    font-size: 3rem;
    font-family: sans-serif;
  }

</style>
