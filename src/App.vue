<template>
  <div class="container mt-5">
    <Counter/>
  </div>
</template>

<script>

import Counter from "@/components/Counter";
export default {
  name: 'App',
  components: {
    Counter
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.container{
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
  @media screen and (min-width: 600px) {
      grid-template-columns: 1fr 1fr;
    gap: 2rem;
  }
  @media screen and (min-width: 1100px) {
      grid-template-columns: 1fr 1fr 1fr;
  }
}
</style>
