<template>
  <div class="row">
    <div class="col-md" v-for="item in movies.items" :key="item.id">
      <div
        class="card border-0"
        style="width: 10rem; height: 25rem; font-size: 13px"
      >
        <img class="card-img-top" :src="item.image" alt="" />

        <div class="list-group list-group-flush">
          <div class="list-group-item" style="height: 5rem">
            <p>{{ item.title }}</p>
          </div>

          <div class="list-group-item dropdown">
            <button
              class="btn btn-dark dropdown-toggle m-0 p-1"
              type="button"
              id="dropdownMenuButton1"
              data-bs-toggle="dropdown"
              aria-expanded="false"
            >
              More Info
            </button>

            <h6 class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
              {{ item.crew }}
            </h6>
          </div>
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
