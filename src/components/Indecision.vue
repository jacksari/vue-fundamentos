<template>
  <img class="img-fluid" :src="image ? image : 'https://via.placeholder.com/250'" alt="Imagen de prueba">
  <div class="bg-dark">

  </div>
  <div class="indecision-container">
    <input v-model="question" type="text" placeholder="Realiza una pregunta"/>
    <p class="mt-2">Recuerda terminar con un signo de interrogación (?)</p>
    <div v-if="isValid">
      <h2>{{ question }}</h2>
      <h1>{{ getYes }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: "Indecision",
  data () {
    return {
      question: null,
      answer: null,
      image: null,
      isValid: false
    }
  },
  methods: {
    async getAnswer() {
      this.answer = 'Pensando...';
      const data = await fetch('https://yesno.wtf/api').then(r => r.json());
      //console.log(data)
      this.answer = data.answer;
      this.image = data.image;
    }
  },
  computed: {
    getYes(){
      return this.answer === 'yes' ? 'Si' : 'No';
    }
  },
  watch: {
    question(value, oldValue) {
      this.isValid = false;
      if(value === ''){
        this.answer = null;
        this.image = null
      }
      if(!value.includes('?')) return;
      this.isValid = true;
      // Realizar petición http
      this.getAnswer();
    }
  }
}
</script>

<style scoped>
.container{
}
.img-fluid{
}
img, .bg-dark {
  height: 100vh;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
  object-fit: cover;
}

.bg-dark {
  background-color: rgba(0, 0, 0, 0.4) !important;
}

.indecision-container {
  text-align: center;
  position: relative;
  z-index: 99;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}
input:focus {
  outline: none;
}

p {
  color: white;
  font-size: 20px;
  margin-top: 0px;
}

h1, h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}

</style>
