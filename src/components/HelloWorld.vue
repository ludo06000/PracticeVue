<script>
export default {
    name: "HelloWorld",
    props: {
      msg: String,
    },
    data() {
      return{
        imagePanier : 'https://imgs.search.brave.com/4CiufIv3hvPFcemo0GqqjKkr_o2bSpDuuMLGjDBirOc/rs:fit:800:566:1/g:ce/aHR0cHM6Ly9zdXBl/cmF3ZXNvbWV2ZWN0/b3JzLmNvbS93cC1j/b250ZW50L3VwbG9h/ZHMvMjAxNi8wMi9z/aG9wcGluZy1iYXNr/ZXQtaWNvbi5qcGc'
      }
    }
}

</script>

<template>
  <h1>{{ msg }}</h1>
  <img class="panier" v-bind:src="imagePanier">

</template>

<style scoped>

</style>
