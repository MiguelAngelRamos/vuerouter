<template>
  <div class="container mt-5">
    <h2 class="fst-italic text-center mb-5">Lista de Posts</h2>

    <div class="row" v-for="post in posts" :key="post.id">

      <div class="col posts">

        <h1>{{ post.title.charAt(0).toUpperCase() + post.title.slice(1)}}</h1>
       
        <router-link :to="`/user/${post.userId}`">Autor</router-link>
        <p> {{ post.body }}</p>
        <button class="btn btn-secondary" @click="comentariosid(post.id)">Ver comentarios</button>
        <!-- Comentarios de los Posts -->
        <template v-for="comentFiltro in comentariosFiltrados" :key="comentFiltro.id">
          <div class="mt-3 col-sm-10 offset-sm-1" v-if="comentFiltro.postId === post.id">
            <label class="fw-bold"> User: {{ comentFiltro.email }}</label>
            <br>
            <label class="fw-bold"> Respuesta: </label>
            <p> {{ comentFiltro.body }}</p>
          </div>

        </template>
        <hr>
      </div>

    </div>

  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
  },
  data() {
      return {
        posts: [],
        comentarios: [],
        comentariosFiltrados: []
      }
    },
    methods: {
      /* Filtramos comentarios, que pertenecen a un post en particular, por medio de la ID del Posteo */
      comentariosid(id) {
        this.comentariosFiltrados = this.comentarios.filter( comentarios => comentarios.postId === id);
        console.log(this.comentariosFiltrados);
      },
      async consumirPosts() {
        try {
          const data = await fetch(`https://jsonplaceholder.typicode.com/posts`);
          const getPosts = await data.json();
          this.posts = getPosts;
          console.log(this.posts);
        } catch (error) {
          console.log(error);
        }
      },
      async consumirComentarios() {
        try {
          const data = await fetch(`https://jsonplaceholder.typicode.com/comments`);
          const getComentarios = await data.json();
          this.comentarios = getComentarios;
          console.log(this.comentarios)
        } catch (error) {
          console.log(error);
        }
      }
    },
    created() {
      this.consumirPosts();
      this.consumirComentarios();
    }
}
</script>

<style scoped>
  h1 {
    font-size:  x !important;
  }

  a {
    text-decoration: none;
    color: #524e4e;
    background-color: bisque;
    padding: 2px 7px;
  }
</style>