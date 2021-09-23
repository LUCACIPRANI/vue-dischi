<template>
  <div class="loader">
    <svg
      xmlns="http://www.w3.org/2000/svg"
      aria-hidden="true"
      focusable="false"
      data-prefix="fas"
      data-icon="music"
      class="svg-inline--fa fa-music fa-w-16"
      role="img"
      viewBox="0 0 512 512"
    >
      <path
        fill="currentColor"
        d="M470.38 1.51L150.41 96A32 32 0 0 0 128 126.51v261.41A139 139 0 0 0 96 384c-53 0-96 28.66-96 64s43 64 96 64 96-28.66 96-64V214.32l256-75v184.61a138.4 138.4 0 0 0-32-3.93c-53 0-96 28.66-96 64s43 64 96 64 96-28.65 96-64V32a32 32 0 0 0-41.62-30.49z"
      />
    </svg>

    <div class="text">Loading...</div>
  </div>
</template>

<script>
export default {
  name: "Loader",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../style/vars";
@import "../style/mixin";


.loader {
  position: fixed;
  top: 0;
  left: 0;
  @include center();
  flex-direction: column;
  width: 100%;
  height: 100%;
  background-color: $primarycolor;
  color: white;
  svg {
    width: 70px;
    margin: 3rem 0;
    animation: pulse 1s infinite alternate;
  }
  .text {
    animation: pulse 1s ease-out forwards;
  }

  @keyframes pulse {
    from {
      transform: scale(1);
    }
    to {
      transform: scale(2);
    }
  }
}
</style>
