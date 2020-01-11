<template>
  <div class="claimWrapper">
    <h1 class="claim">Movies</h1>
    <p class="sublaim">Podaj nazwę filmu, który chcesz podejrzeć.</p>
  </div>
</template>

<script>

export default {
  name: 'Claim',
};
</script>

<style lang="scss" scoped>
    .claimWrapper {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      color: #fff;

      .claim {
        font-size: 52px;
        text-align: center;

        @media (min-width: 768px) {
          font-size: 78px;
        }

        @media (min-width: 1024px) {
          font-size: 100px;
        }
      }

      .subclaim {
        margin: 20px 0 0 0;
        font-size: 14px;
        font-weight: 400;
        text-align: center;

        @media (min-width: 768px) {
          font-size: 18px;
          width: 500px;
          letter-spacing: 1px;
          line-height: 1;
        }
      }
    }
</style>
