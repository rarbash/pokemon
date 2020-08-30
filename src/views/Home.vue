<template>
  <div class="home">
    <nav aria-label="Page navigation example">
      <ul class="pagination">
        <li class="page-item">
          <a class="page-link" v-on:click="beforePage()">Previous</a>
        </li>
        <li
          class="page-item"
          v-for="(totalPage, page) in totalPages.slice(currentPage,currentPage+10)"
          :key="page"
        >
          <!-- <a v-if="page > 3" class="page-link" v-on:click="nextPage()">...</a> -->
          <a
            class="page-link"
            v-on:click="changePage(totalPage)"
            :active="page === currentPage"
          >{{ totalPage + 1 }}</a>
        </li>
        <li class="page-item">
          <a class="page-link" v-on:click="nextPage()">Next</a>
        </li>
      </ul>
    </nav>
    <Template
      :pokemonlists="pokemonList"
      :pokemonImgList="pokemonImgList"
      v-if="pokemonList.length !== 0"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import Template from "@/components/Template.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Template,
  },
  data() {
    return {
      pokemonList: [],
      pokemonImgList: [],
      currentPage: 0,
      perPage: 20,
      totalItems: 0,
      totalPages: [],
      totalPageNum: 0,
    };
  },
  watch: {
    data() {
      this.currentPage;
    },
  },
  async mounted() {
    await this.getPokemonApi();
    this.pagination();
  },
  methods: {
    async getPokemonApi() {
      try {
        const response = await axios.get(
          `https://pokeapi.co/api/v2/pokemon/?offset=${
            this.currentPage * this.perPage
          }&limit=${this.perPage}`
        );
        this.pokemonList = response.data.results;
        this.totalItems = response.data.count;

        this.pokemonImgList = [];
        for (let i = 0; i < this.perPage; i++) {
          const responseImg = await axios.get(response.data.results[i].url);
          this.pokemonImgList.push(responseImg.data.sprites.front_default);
        }
      } catch (error) {
        console.log(error);
      }
    },
    pagination() {
      this.totalPageNum = Math.floor(this.totalItems / this.perPage);
      for (let i = 1; i <= this.totalPageNum; i++) {
        this.totalPages.push(i);
      }
      return this.totalPages;
    },
    changePage(page) {
      this.currentPage = page;
      this.pageActive = this.currentPage;
      this.getPokemonApi();
    },
    beforePage() {
      if (this.currentPage !== 0) {
        this.currentPage--;
        this.getPokemonApi();
      }
    },
    nextPage() {
      if (this.currentPage < this.totalPageNum) {
        console.log(this.currentPage);
        this.currentPage++;
        this.getPokemonApi();
      }
    },
    // minPagination() {
    //   return this.currentPage + 4;
    // },
    // maxPagination() {
    //   return this.currentPage + 10;
    // }
  },
};
</script>

<style>
a:active {
  background: pink;
}
a:hover {
  color: hotpink;
}
</style>
