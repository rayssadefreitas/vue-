<template>

  <header>
    <hr>
    <p>Color Tintas</p>
    <hr>
  </header>
  <section>
    <div>
      <p>Qual a área que deseja pintar?(m2)</p>
      <input type="number" v-model="area">
      <button v-on:click='calcular()'>Calcular</button>
    </div>
  </section>
  <section class='resultados'>
    <div class='total'>
      <p>Quantidade de latas de 18 litros: {{latas}}</p>
      <p>Quantidade de galões de 3,6 litros: {{galoes}}</p>
      <p>Valor total: {{total}}</p>
    </div>
  </section>
 
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      area:0,
      latas:0,
      galoes:0,
      total:0
    }
  },
  methods:{
    calcular(){
     let litros = this.area/6;
     if(litros%18==0){
        this.latas = litros/18;
        this.galoes = 0;
        this.total = this.latas*80;
      }
      else if(litros%18!=0){
        this.latas = Math.floor(litros/18);
        this.galoes = Math.ceil((litros%18)/3.6);
        this.total = (this.latas*80)+(this.galoes*25);
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
  font-size: 30px;
}
header{
  background-image: linear-gradient(to right, #5b28de 0%, #a6c1ee 51%, #9a78f2 100%);
  position: static;
}
input{
  width: 70vw;
  height: 70px;
  border-radius: 5px;
  border: 1px solid rgb(164, 17, 127);
}
button:hover{
  filter: drop-shadow(0 0 0.75rem #de2828);
  transition: 0.2s ease-in-out;
}
button{
  width: 200px;
  height: 100px;
  margin-left: 5px;
  border-radius:5px;
  border: 1px solid rgb(164, 17, 68);
  background-color: #eea6d7;
  color: #502c49;
  cursor: pointer;
  text-align: center;
}
.resultados{
  margin:15px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.total{
  display: flex;
  width: 70%;
  height: 90%;
  cursor: pointer;
}
.total p{
  font-size: 15px;
   color: #4c2c50;
  border-radius:7px;
  border: 1px solid rgb(105, 17, 164);
  width: 50vw;
}
</style>
