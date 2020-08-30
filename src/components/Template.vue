<template>
  <div class="template">
    <div class="row">
      <div class="col-md-3" v-for="(pokemonlist, id) in pokemonlists" :key="id">
        <b-card>
          <div v-if="pokemonImgList[id] !== null">
            <img :src="pokemonImgList[id]" alt="pokemon_img" />
          </div>
          <div v-else>
            <img src="../assets/noImg.png" alt="pokemon_img" />
          </div>
          <h2 class="text-capitalize">{{ pokemonlist.name }}</h2>
        </b-card>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    pokemonlists: Array,
    pokemonImgList: Array
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.template {
  background-color: #f3cb6b;
  opacity: 0.8;
  width: 80%;
  margin-left: 10%;
  margin-top: 3%;
  border-radius: 8px;
  padding: 2%;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
}
img {
  max-width: 100%;
  height: 200px;
}
h2 {
  height: 50px;
  background: #747474;
  border-radius: 8px;
  color: whitesmoke;
  padding-top: 8%;
  font-size: 20px;
  margin-top: 3%;
}
h1 {
  color: #9f4c04;
}
.card {
  background: whitesmoke;
  margin: 2%;
  margin-right: 0%;
  margin-bottom: 11%;
  padding: 2%;
  border-radius: 8px;
  box-shadow: 5px 4px 8px 2px rgba(70, 69, 69, 0.2);
}
.card:hover {
  transform: scale(1.05);
  color: gray;
  opacity: 1;
}
</style>
