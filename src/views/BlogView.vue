<script>
import TituloVue from "../components/TituloVue.vue";

export default {
  components: {
    TituloVue,
  },
  data() {
    return {
      arrayBlog: [],
    };
  },
  methods: {
    async getApi() {

      //obtener la api dando click no es del todo bien porque si queremos ver info tenemos que darle click,por lo que si usamos el ciclo de vida de vueJs podemos hacer que apenas se renderice la vista que obtenga la info pa

      try {
        const data = await fetch("https://jsonplaceholder.typicode.com/posts");

        const array = await data.json();
        this.arrayBlog = array;

        console.log(this.arrayBlog);
      } catch (error) {
        console.log(error);
      }
    },
  },

  created(){
    //apenas se cree nuestra app vamos a ejecutar funciones pa aqui solo se llaman funciones , nada de declara funciones que te meto un calvazo

    this.getApi()
  
  }
};
</script>

<template>
  <div>
    <TituloVue texto="Titulo de mi Blog" />
    <button @click="getApi">Consumir Api</button>
    <div v-for="post in arrayBlog" :key="post.id">
      <router-link :to="`/blog/${ post.id }`">
        {{post.title }}
      </router-link>
    </div>
  </div>
</template>

<style></style>
