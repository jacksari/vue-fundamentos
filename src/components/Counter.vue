<template >
  <div class="bg-primary p-2 text-light rounded text-center">
    <h2>{{ customTitle }}</h2>
    <p>{{ counter }} <sup>2</sup> = {{ getSquareValue }}</p>
    <div class="">
      <button class="btn btn-success mx-2" @click="increment">Increment</button>
      <button class="btn btn-success mx-2" @click="reset">Reset</button>
      <button class="btn btn-success mx-2" @click="decrement">Decrement</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Counter",
  data() {
    return {
      counter: this.num,
    }
  },
  props: {
    num: {
      type: Number,
      default: 5,
      validator(value) {
        //return value < 20
      }
    },
    title: String
  },
  methods: {
    increment() {
      this.counter = this.counter + 1;
    },
    decrement() {
      this.counter = this.counter - 1;
    },
    reset(){
      this.counter = 5
    }
  },
  computed: {
    getSquareValue() {
      return Math.pow(this.counter, 2);
    },
    customTitle(){
      return this.title || 'Counter'
    }
  }
}
</script>

<style scoped lang="scss">

</style>
