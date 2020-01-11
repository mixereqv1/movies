<template>
  <a class="adLink" target="_blank" href="https://www.themoviedb.org/">
    <img src="https://www.themoviedb.org/assets/2/v4/logos/408x161-powered-by-rectangle-green-bb4301c10ddc749b4e79463811a68afebeae66ef43d17bcfd8ff0e60ded7ce99.png" alt="TMDb">
  </a>
</template>

<script>

export default {
  name: 'Ad',
};
</script>

<style lang="scss" scoped>
  .adLink {
    width: 204px;
    height: 80.5px;
    align-self: flex-end;
    margin: 10px auto;

    img {
      width: 100%;
      height: 100%;
    }
  }

  .absoluteBottom {
    position: absolute;
    bottom: 10px;
    left: 50%;
    transform: translateX(-50%);
  }
</style>
