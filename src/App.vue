<template>
<Header/>
  <div class="container">
    <table class="table table-striped table-bordered table-hovered">
      <thead>
        <tr class="cab">
          <th>Id</th>
          <th>Título</th>
          <th>Conteúdo</th>
          <th>Criado</th>
          <th>Atualizado</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(post,) in posts" :key="post.id">
      <!--     <td>{{ index + 1 }}</td> -->
          <td>{{ post.title }}</td>
          <td>{{ post.content }}</td>
          <td>{{ post.created_at }}</td>
           <td>{{ post.updated_at }}</td>
        </tr>
      </tbody>

    </table>
  </div>
  <Footer/>
</template>



<script>
import { onMounted, ref } from "vue";
/* import Card from "./components/Card"; */
import axios from "axios";
import Header from "./components/Header"
import Footer from "./components/Footer";

export default {
  components: { Header, Footer },
  name: "App",
  /*   //components: { Card }, */

  setup() {
    /* //const show = ref(true); */
    const posts = ref([]);
    const loading = ref([false]);
    const error = ref("");

    onMounted(async () => {
      try {
        loading.value = true;
        const response = await axios.get(
          "https://myapil8.herokuapp.com/api/post"
        );

        //console.log(response.data);
        posts.value = response.data.data;
        loading.value = false;
      } catch (err) {
        console.log(err);
        error.value = "Provavelmente sua rede de internet não está ativa!";
        loading.value = false;
        //alert(error);
      }
    });

    /* 
    const helloworld = () => {
      alert("Hello World!");
    };

    const toggleList = () => {
      show.value = !show.value;
    }; */

    return {
      // helloworld,
      posts,
      // show,
      // toggleList,
      loading,
      error,
    };
  },
};
</script>

<style>
body {
  padding: 0;
  margin: 0;
}
.text-danger {
  color: red;
}

.cab {
  color: blue;
}
</style>
