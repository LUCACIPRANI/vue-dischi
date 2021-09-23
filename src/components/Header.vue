<template>
  <header class="mb-5">
    <img src="@/assets/logo-spotify.png" alt="">
  </header>
</template>

<script>
export default {
  name: 'Header',

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "@/style/mixin";
@import "@/style/general";
@import "@/style/vars";

  header{
    height: 7vh;
    background-color: #2D3B46;
    @include startJC();
    img{
      object-fit: contain;
      height: 60px;
      width: 60px;
      padding: 10px;
    }
  }
</style>
