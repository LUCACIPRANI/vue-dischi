<template>
  <header class="header mb-5 px-3">
    <div>
      <img src="@/assets/logo-spotify.png" alt="" />
    </div>
    <!-- CHOICE GENRE  -->
    <div class="select">
      <!-- GENRE  -->
      <select
        class="d-flex my-5"
        name="select"
        id="select-genres"
        v-model="inputText"
        @change="$emit('selectedOption', inputText)"
      > 
        <option>Select Genres</option>
        <option
          v-for="(genre, index) in arrayGenres"
          :key="index"
          :value="genre"
          >{{ genre }}
        </option>
      </select>
    </div>

  </header>
</template>

<script>
export default {
  name: "Header",
  props: ["arrayGenres"],
  data() {
    return {
      inputText: "",
    };
  },
  mounted() {
    console.log(this.arrayGenres);
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "@/styles/mixin.scss";
@import "@/styles/general.scss";
@import "@/styles/vars.scss";

.header {
  height: 7vh;
  background-color: $thirdcolor;
  @include spBetw();
  img {
    object-fit: contain;
    height: 60px;
    width: 60px;
    padding: 10px;
  }
}

select,
option {
  width: 130px;
  font-weight: 600;
  font-size: 80%;
  border-radius: 20px;
  background-color: $secondcolor;
  
  &:hover {
    border: 1px solid white;
    color: black;
    cursor: pointer;
  }
}
</style>
