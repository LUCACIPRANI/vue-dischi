<template>
  <section class="container">
    <div v-if="!loading" class="row mx-5">
      <div
        v-for="(disc, index) in DiscsList"
        :key="index"
        class="col-6 col-md-3 col-lg-3 mb-3"
      >
        <Discs :discoProp="disc" />
      </div>
    </div>
    <Loader v-else />
  </section>
</template>

<script>
import axios from "axios";
import Discs from "./Discs.vue";
import Loader from "./Loader.vue";

export default {
  name: "Main",
  components: {
    Discs,
    Loader,
  },
  data() {
    return {
      APIUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      DiscsList: [],
      loading: true,
    };
  },
  created() {
    this.getDiscs();
  },
  methods: {
    getDiscs() {
      axios
        .get(this.APIUrl)
        .then((res) => {
          this.DiscsList = res.data.response;
          setTimeout(() => {
            this.loading = false;
          }, 5000);
          // console.log(res.data.response);
        })
        .catch((err) => {
          console.log("Error ", err);
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "@/style/mixin";
@import "@/style/general";
@import "@/style/vars";
</style>
