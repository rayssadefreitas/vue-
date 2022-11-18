<template>
  <h3> JORGE'S PIZZAS </h3>
  <h2> Descubra a quantidade certa de pizzas para seu evento '=' </h2>
  <img mt-4 src  ="https://www.receitasdepesos.com.br/wp-content/uploads/2020/10/pizza-de-frigideira-receita-scaled.jpg">
  <div class ='pessoas'>
        <h3>Quantidade de adultos</h3>
        <input  type="number" placeholder="Digite a quantidade de adultos" v-model='adultos'>
        <h3>Quantidade de crianças</h3>
        <input type="number" placeholder="Digite a quantidade de crianças" v-model="criancas">
   </div>
  <button v-on:click="calcular()">Calcular</button>
  <p>
 Quantidade de pizzas gigantes(12):{{quantidadeDePizza12}}
  </p>
  <p>
    Quantidade de pizzas média(10):{{quantidadeDePizza10}} 
  </p>
  <p>
    Quantidade de pizzas pequena(8):{{quantidadeDePizza8}} 
  </p>
  
</template>
<script>
  export default {
    name: 'App',
    data(){
        return{
            adultos: 0,
            criancas: 0,
            quantidadeDePedacosAdulto:0,
            quantidadeDePedacosCrianca:0,
            quantidadeDePizza12 : 0,
            quantidadeDePizza10 : 0,
            quantidadeDePizza8 : 0,
        }
    },
    methods : {
        calcular(){
            let resto;
            
            this.quantidadeDePedacosAdulto = this.adultos * 3;
            this.quantidadeDePedacosCrianca = this.criancas * 2;
            let totalDePedacos = (this.quantidadeDePedacosAdulto) + (this.quantidadeDePedacosCrianca);
            this.quantidadeDePizza12 = parseInt(totalDePedacos / 12);
            resto = totalDePedacos % 12;
            this.quantidadeDePizza10 = parseInt(resto / 10);
            resto = resto % 10;
             this.quantidadeDePizza8 = parseInt(resto / 8);
            resto = resto % 8;
            if(resto > 0){
                this.quantidadeDePizza8++;
            }
        }
    }
  }
 
</script>
<style scoped>
  h3{
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;

background-image: -moz-repeating-radial-gradient(rgb(198, 73, 93));
    text-align: center;
    color: #000000;
    height: 20px;
    
  }
  button{
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 30px;
    margin-left: 30px;
    margin-right: 30px;
    padding: 30px;
    width: 200px;
    border: 2px solid rgb(237, 163, 210);
    border-radius: 5px;
   background-color:rgb(237, 163, 210);
    color: #000000;
    font-size: 20px;
    font-weight: bold;
  }
   .pessoas{
        display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
        margin-top: 10px;
        margin-left: 10px;
        margin-right: 20px;
        padding: 30px;
        width: 50vw;
        border: 2px solid rgb(237, 163, 210);;
        border-radius: 10px;
           }
    .pessoas h3{
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        text-align: center;
        color: #000000;
    }
    .pessoas input{
        width: 50%;
        height: 40px;
        border: 4px solid #aa0444;
        border-radius: 10px;
        padding: 10px;
        font-size: 20px;
        background-color: #e2acc1;
        float: left;
         
         }
    img{
      width: 600px;
      height: 400px;
       float: right;

    }
</style>