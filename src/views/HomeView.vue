<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <TituloVue texto="Hola desde Hom"/>
  </div>
</template>

<script>
import TituloVue from '@/components/TituloVue.vue'
// @ is an alias to /src


export default {
  name: 'HomeView',
  components: {
    TituloVue
  }
}
</script>
