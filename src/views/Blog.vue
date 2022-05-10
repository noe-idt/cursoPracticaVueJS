<template>
  <div class="home">
    <Titulo texto="Blog"></Titulo>
  </div>

  <ul v-for="post in posts" :key="post.userId">
  
    <li>User : {{ post.userId }}</li>
    <li>POST No. {{ post.id }}</li>
    <li><router-link :to=" `/blog/${post.id}` ">{{ post.title }}</router-link></li>
  </ul>
</template>
<script>
// @ is an alias to /src
import Titulo from "../components/Titulo";
export default {
  name: "Blog-item",
  components: {
    Titulo,
  },
  data() {
    return {
      posts: [],
    };
  },
  methods: {
    async consumirApi() {
      try {
        const data = await fetch("https://jsonplaceholder.typicode.com/posts");
        const array = await data.json();
        this.posts = array;
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
    this.consumirApi();
  },
};
</script>
