<template>
<div class="Body"> 
    <br>
        <H3 style="color:Red">Convertidor de Masa</H3>
        
    <div class="Main">
        <br>
        <br>    
        <div class="form-group">
				 <font face="Comic Sans MS,arial,verdana"><h6> Ingrese cantidad a convertir:  <input type="number" v-model ="entrada_numero" ></h6></font>
          <br>
				
			</div>
        <div>
            <font face="Comic Sans MS,arial,verdana"><span>De:</span></font>
            <br>
        </div>
        <br>
        <select v-model="convertFrom">
            <br>
            <option value="g">Gramos</option>
            <option value="kg">Kilogramos</option>
            <option value="onz">Onzas</option>
            <option value="lb">Libras</option>
            <option value="T">Toneladas</option>
        </select>
        <div>
            <br>
            <font face="Comic Sans MS,arial,verdana"><span>a:</span></font>
        </div>
        <br>
        <select v-model="convertTo">
            <option value="g">Gramos</option>
            <option value="kg">Kilogramos</option>
            <option value="onz">Onzas</option>
            <option value="lb">Libras</option>
            <option value="T">Toneladas</option>
        </select>
        <br>
        <br>
        <br>
         <font face="Comic Sans MS,arial,verdana"><b-button v-b-modal.modal-1 variant="btn btn-dark" v-on:click="calcular">Convertir</b-button></font>
    </div>
   <div>
  <b-modal id="modal-1" title="Resultado">
    <p class="my-4">El resultado es: {{salida}}</p>
  </b-modal>
</div>
</div>
</template>
<script>
export default ({
    name:"Masa",
    data(){return{
            entrada_numero:"",
            conversiones_gramos:{ "g":1,
                                  "kg":0.001,
                                  "onz":0.03528,
                                  "lb":0.002205,
                                  "T":0.000001102},    
            salida: "",
            convertTo: "g",
            convertFrom:"kg"
        }},
        methods:{
            calcular:function(){
                let convertTo = this.conversiones_gramos[this.convertTo]
                let convertFrom = this.conversiones_gramos[this.convertFrom]
                var resultado = ((convertTo/convertFrom))*this.entrada_numero
                this.salida =resultado         
            }
        }
})
</script>
<style>
.Body {
	background-color: rgb(241, 246, 250);
	background-position: center;
	background-size: cover;
	background-attachment: fixed;
	background-repeat: no-repeat;
}
.Main {
	width: 50vw;
    margin: auto;
    padding: 30px;
    border-radius: 10px;
    border-style: solid;
    border-color:rgb(12, 12, 12);
    background-color: rgba(241, 206, 11, 0.472);
    color: rgb(0, 0, 0);
}
#Resultado h2 {
	font-size: 45px;
}
</style>
