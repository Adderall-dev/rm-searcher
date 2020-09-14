<template>
  <div id="main">
    <!--search input-->
    <div id="search">
      <img src="../assets/rick-144.png" />
      <h1>R&M Searcher</h1>
      <label for="search">Search characters:</label>
      <input
        id="search"
        v-model="searchVal"
        type="text"
        placeholder="eg. Rick"
        @input="handleInput"
      />
    </div>
    <!--Results-->
    <div id="results">
      <ul>
        <li v-for="result in results" :key="result.id">
          <div class="output">
            <img :src="result.image" width="100px" height="100px" />
            <h1>Name: {{ result.name }}</h1>
            <h3>Status: {{ result.status }}</h3>
            <h3>Origin Name: {{ result.origin.name }}</h3>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import debounce from "lodash.debounce";

export default {
  name: "SearchComponent",
  data() {
    return {
      searchVal: "",
      results: [],
    };
  },
  components: {},
  methods: {
    handleInput: debounce(function () {
      axios
        .get(
          `https://rickandmortyapi.com/api/character/?name=${this.searchVal}`
        )
        .then((res) => {
          this.results = res.data.results;
        })
        .catch((err) => console.log(err));
    }, 500),
  },
};
</script>

<style scoped>
#main {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex-wrap: wrap;
  justify-content: space-around;
}
label {
  margin: 5px;
}
#search {
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: space-around;
}
#results li {
  list-style: none;
  height: 50vh;
  margin: 20px;
  border-radius: 10px;
  padding: 3%;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #e6e6e6;
  box-shadow: 0 10px 10px rgba(204, 204, 204, 1);
}
.output {
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: space-around;
}
</style>