<template>
  <main>
  <h1>Calcular IMC</h1>
    <form>
       <label for="peso">Peso</label>
        <input type="text" id="peso" autofocus @input="addPeso($event.target.value)">
        <label for="altura">Altura</label>
        <input type="text" id="altura" autofocus @input="addAltura($event.target.value)">
      <button type="button" @click="calculoImc()">Calcular</button>
         <span> {{error}}</span>
      <p class="resultado">Seu IMC: <strong>{{imc}}</strong></p>
    </form>
  </main>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      peso: '',
      altura: '',
      imc: '',
      error: '',
      resultTable: ''

    }
  },
  methods: {
    addPeso: function(peso) {
  this.error = ''
      this.peso =  parseFloat(peso);
    },
    addAltura: function(altura) {
      this.error = ''
      this.altura =  parseFloat(altura);
    },
    calculoImc: function(){
      if(!this.peso || !this.altura) {
        this.error = "Por favor preencher todos os campos.";
        return;
      }
      this.imc = (this.peso / (this.altura * this.altura)).toFixed(2)
    }
  },
}
</script>

<style>
  body {
    background: #C71585;
    background: -webkit-linear-gradient(top, rgba(255,93,177,1) 0%, rgba(199,21,134,1) 100%);
    background: -o-linear-gradient(top, rgba(255,93,177,1) 0%, rgba(199,21,134,1) 100%);
    background: -ms-linear-gradient(top, rgba(255,93,177,1) 0%, rgba(199,21,134,1) 100%);
    background: linear-gradient(to bottom, rgba(255,93,177,1) 0%, rgba(199,21,134,1) 100%);
    background-repeat: no-repeat;
    height: 700px;
    margin: 0 auto;

    display: flex;
    flex-direction: column;
    align-items: center;
    font-size: 23px;
  }
  h1 {
    margin: 0;
    text-align: center;
    margin-bottom: 1em;
    color: #fff;
  }
  button {
    background-color: #C71585;
    color: #fff;
    border: none;
    padding: .5em 1em;
  }
  .resultado {
    background-color: #fff;
    color: #C71585;
    padding: .5em;
  }
  span {
    color: #fff;
    font-size:.8em;
  }
  label {
    color: #fff;
  }
  input {
    padding: .5em;
    border: none;
  }
</style>
