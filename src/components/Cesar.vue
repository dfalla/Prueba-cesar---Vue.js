<template>
  <div id="myApp">
    <label for="palabra">Palabra</label>
        <input
          type="text"
          class="palabra"
          v-model="palabra"
          v-on:keyup="mayuscula"
        >
        <label for="palabra">Desplazamiento</label>
        <input
          type="text"
          class="desplazamiento"
          v-model="desplazamiento"
        >
        <button class="cifrar" @click="cifrar">Cifrar</button>
        <label for="palabraCifrada">Palabra cifrada</label>
        <input
          type="text"
          class="palabraCifrada"
          disabled
          v-model="palabraCifrada"
        >
  </div>
</template>

<script>
export default {
    name: 'Cesar',
    data(){
        return{
            palabra: '',
            palabraCifrada: '',
            desplazamiento: null
        }
    },
    methods: {
        mayuscula(){
            this.palabra = this.palabra.toUpperCase();
        },
        cifrar(){
          const texto = this.palabra;
          if(!texto) return;
          const letras = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
          this.desplazamiento = (this.desplazamiento % 26 + 26) % 26;
          this.palabraCifrada = texto.replace(/[A-Z]/ig, c => letras[(letras.indexOf(c) + this.desplazamiento)%26]);
        }
    }
}
</script>

<style>
*{
    margin: 0;
    box-sizing: border-box;
}

body{
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-color: gray;
}
#myApp{
    width: 200px;
    height: 260px;
    background-color: white;
    border-radius: 10px;
    text-align: center;
}

label{
    font-weight: bold;
    display: block;
    margin-top: 20px;
    margin-bottom: 10px;
}

input{
    text-align: center;
    color: black;
    font-weight: bold;
}

.palabra{
    display: block;
    margin: auto;
    margin-bottom: 25px;
}

.palabraCifrada{
    display: block;
    margin: auto;

}

.cifrar{
    display: block;
    margin: auto;
    margin-top: 15px;
}


</style>