<template>
  <div class="container mt-5">
    <h2 class="fst-italic text-center mb-5">Lista de Posts</h2>
    <div class="row" v-for="post in posts" :key="post.id">
      <div class="col posts">
        <h1>{{ post.title.charAt(0).toUpperCase() + post.title.slice(1)}}</h1>
        <router-link :to="`/user/${post.userId}`">Autor</router-link>
        <p> {{ post.body }}</p>
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
        comentarios: []
      }
    },
    methods: {
      async consumirPosts() {
        try {
          const data = await fetch(`https://jsonplaceholder.typicode.com/posts`);
          const getPosts = await data.json();
          this.posts = getPosts;
          console.log(this.posts);
        } catch (error) {
          console.log(error);
        }
      }
    },
    created() {
      this.consumirPosts();
    }
}
</script>
