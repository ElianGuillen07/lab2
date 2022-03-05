<template>
    <div class="body">
        <br>
        <br>
         <H3 style="color:Red">Convertidor de Masa</H3>
         <br>
         <br>
      <div class="main"> 
          <h6>Ingrese el número:  <input type="number" v-model ="vl" ></h6> 
          <br><br>
        
           <h6>Seleccione la medida:  <select v-model="pasarDe">
         
            <option value="b">byte</option>
            <option value="KB">KiloByte</option>
            <option value="MB">MegaByte</option>
            <option value="GB">GigaByte</option>
            <option value="TB">TeraByte</option>
            <option value="PB">PetaByte</option>
            <option value="EB">ExaByte</option>
        </select></h6> 
        <br><br>
       
    
            <h6>Seleccione la medida a convertir:   <select v-model="pasarA">
          <option value="b">byte</option>
            <option value="KB">KiloByte</option>
            <option value="MB">MegaByte</option>
            <option value="GB">GigaByte</option>
            <option value="TB">TeraByte</option>
            <option value="PB">PetaByte</option>
            <option value="EB">ExaByte</option>

        </select></h6> 
        <br><br>
        <div>
        <b-button v-b-modal.modal-1 variant="btn btn-dark" v-on:click="conversion">Convertir</b-button>
  <b-modal id="modal-1" title="Resultado">
    <p class="my-4">El resultado de la conversión es: {{res}}</p>
  </b-modal>
</div>
     </div>
      </div>
</template>

<script>
export default({
    name:"almacenamiento",
    data(){return{
            vl:"",
            valores_conversiones:{
                "b":1073741824,
                "kb":1048576,
                "MB":1024,
                "GB":1,
                "TB":0.000977,
                "PB":0.000000954,
                "EB":0.000000000931,
                },    
            res: "",
            pasarDe: "b",
            pasarA:"GB"
        }},
    methods:{
            conversion:function(){
                let pasarA = this.valores_conversiones[this.pasarDe]
                let pasarDe = this.valores_conversiones[this.pasarA]
                var resultado = ((pasarDe/pasarA))*this.vl
                this.res =resultado
            }
        }
})
</script>
<style>

.main {
    width: 50vw;
    margin: auto;
    padding: 30px;
    border-radius: 10px;
    border-style: solid;
    border-color:rgb(12, 12, 12);
    background-color: rgba(241, 206, 11, 0.472);
    color: rgb(0, 0, 0);
}
</style>
