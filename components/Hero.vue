<template>
  <div class="hero">
    <img src="../assets/images/background.jpg" alt="" />
    <div class="header-container">
      <div class="header-text">
        <h1>Now Streaming</h1>
        <a href="#" class="button">View Movies</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Hero',
}
</script>

<style lang="scss" scoped>
.hero {
  height: 300px;
  position: relative;

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .header-container {
    z-index: 1;
    position: absolute;
    top: 0;
    margin: 0;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;

    .header-text {
      color: var(--text-white);
    }
  }

  h1 {
    font-size: calc(var(--font-size-base) * 3);
    margin-bottom: var(--spacing-base);
  }
}
</style>
