<template>
  <div class="container container2 p-5">
    <Indecision/>
  </div>
</template>

<script>
import Indecision from "@/components/Indecision";
export default {
  name: 'App',
  components: {
    Indecision
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

  min-height: 100vh;
  @media screen and (min-width: 600px) {
      grid-template-columns: 1fr 1fr;
    gap: 2rem;
  }
  @media screen and (min-width: 1100px) {
      grid-template-columns: 1fr 1fr 1fr;
  }
}
.container2{
  grid-template-columns: 1fr;
}
</style>
