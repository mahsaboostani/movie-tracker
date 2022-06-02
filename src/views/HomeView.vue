<template>
  <div class="row">
    <div class="col-md" v-for="item in movies.items" :key="item.id">
      <div class="card border-0 justify-content-center" style="width: 10rem">
        <img class="card-img-top" :src="item.image" alt="" />
        <div class="card-body">
          <p>{{ item.fullTitle }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
export default {
  name: "HomeView",
  mounted() {
    axios
      .get(" https://imdb-api.com/en/API/Top250Movies/k_v8ot5y0a")
      .then((response) => {
        this.movies = response.data;
        console.log(response.data);
      })
      .catch(function (error) {
        console.error(error);
      });
  },
  data() {
    return {
      movies: [],
    };
  },
};
</script>
