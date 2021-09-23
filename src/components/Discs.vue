<template>
<!-- <div class="container-d"> -->
  <div class="Discs">
    <img class="img-fluid mt-4" :src="discoProp.poster" :alt="discoProp.title">
    <h6 class="pt-3 px-3">{{ discoProp.title.toUpperCase() }}</h6>
    <div class="second-color">{{ discoProp.author }}</div>
    <div class="second-color">{{ discoProp.year }}</div>
  </div>
<!-- </div> -->
</template>

<script>
export default {
  name: "Discs",
  props: ["discoProp"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "@/style/mixin";
@import "@/style/general";
@import "@/style/vars";

.Discs{
  background-color: #2D3B46;
  height: 300px;
  width: 170px;
  text-align: center;
  color: white;
  padding: 0 20px;
  img{
    height: 130px;
    width: 130px;
  }
  .second-color{
    color: $secondcolor;
    font-size: 15px;
  }
  h6{
    font-weight: 700;
  }
}

@media only screen and (min-width: 600px )  {
  .container-d {
    width: calc(100% / 5);
  }
}

</style>
