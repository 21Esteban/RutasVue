<template>
  <TituloVue texto="ruta con parametros"/>
  <h2>Parametro {{ $route.params.id }}</h2>
    <div>
        <h1>{{ info.title }}</h1>
        <h2>{{info.body}}</h2>
    </div>
</template>

<script>
import TituloVue from '@/components/TituloVue.vue'

export default {
    components:{
        TituloVue
    },
    data(){
        return{
            info:{},
        }
    },
    methods:{
      async  getApiPa(){
            const infoPa = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`).then(respuesta=> respuesta.json())

        this.info = infoPa

        console.log(this.info);
        }
    },
    created(){
        this.getApiPa();
    }
}
</script>

<style>

</style>