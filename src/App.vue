<template>
  <div id="app">
    <!-- header  -->
    <Header :arrayGenres="genresArray" @selectedOption="getSelection" />
    <!-- main  -->
    <Main @createdGenres="getGenres" :userSelection="userSelection" />
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      selectOption: "",
      genresArray: [],
      userSelection: "",
    };
  },
  props: ["selectedOption", "selectedAuthorOption"],
  methods: {
    getGenres(array) {
      this.genresArray = array;
      console.log(this.genresArray);
    },
    getSelection(text) {
      this.userSelection = text;
      console.log(this.userSelection);
    },
  },
  mounted() {},
  created() {
    this.getGenres;
  },
};
</script>

<style lang="scss">
@import "@/styles/general.scss";
h1 {
  color: white;
}
</style>
