<template>
  <div class="hero">
    <img src="../assets/images/background.jpg" alt="" />
    <div>
      <div>
        <span>Now Streaming</span>
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

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>
