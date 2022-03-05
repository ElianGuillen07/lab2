<template>
  <div>
    <div class="container pt-3">
      <div class="row">
        <div class="col-lg-12">
          <br>
          <br>
          <div class="form-group">
            <br>
            <H3 style="color:Red">Ingrese cantidad</H3>
            <br>
            <input
            
              type="number"
              class="form-control form-control-lg"
              id="cantidad"
              placeholder="Ingrese cantidad.."
              v-model="cantidad"
              v-on:keyup="onChange"
            />
            <br>
          </div>
        </div>
      </div>
      <br>
      <div class="row">
        <div class="col-lg-6">
          <div class="form-group">
            <label for="tengo">Dispongo</label>
            <select
              class="form-control form-control-lg"
              id="tengo"
              v-model="tengo"
              v-on:change="onChange()"
            >
              <option v-for="(moneda, index) in monedas" v-bind:key="index">
                {{ moneda }}
              </option>
            </select>
          </div>
        </div>
        <div class="col-lg-6">
          <div class="form-group">
            <label for="quiero">Deseo</label>
            <select
              class="form-control form-control-lg"
              id="quiero"
              v-model="quiero"
              v-on:change="onChange()"
            >
              <option v-for="(moneda, index) in monedas" v-bind:key="index">
                {{ moneda }}
              </option>
            </select>
          </div>
        </div>
      </div>
      <div class="text-center pt-4">
        <h5 v-if="cantidad > 0">
          <span class="badge badge-success" style="color:White">{{ cantidad }} {{ tengo }}</span>
          <span class="badge badge-dark" style="color:White"> SON </span>
          <span class="badge badge-success" style="color:White">{{ getTotal(total) }} {{ quiero }}</span>
        </h5>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      monedas: ["USD", "EUR", "LIBRA"],
      cantidad: 0,
      tengo: "USD",
      quiero: "EUR",
      total: 0,
    };
  },
  methods: {
    onChange() {
      switch (this.tengo) {
        // Usuario selecciono que tiene dolares
        case "USD":
          if (this.quiero === "USD") {
            this.total = this.cantidad;
          }
          if (this.quiero === "EUR") {
            this.total = this.cantidad * 0.84;
          }
          if (this.quiero === "LIBRA") {
            this.total = this.cantidad * 0.75;
          }
          break;
        // Usuario selecciono que tiene euros
        case "EUR":
          if (this.quiero === "USD") {
            this.total = this.cantidad * 1.19;
          }
          if (this.quiero === "EUR") {
            this.total = this.cantidad;
          }
          if (this.quiero === "LIBRA") {
            this.total = this.cantidad * 0.89;
          }
          break;
          // Usuario selecciono libra
        case "LIBRA":
          if (this.quiero === "USD") {
            this.total = this.cantidad * 1.33;
          }
          if (this.quiero === "EUR") {
            this.total = this.cantidad * 1.12;
          }
          if (this.quiero === "LIBRA") {
            this.total = this.cantidad;
          }
          break;
        default:
      }
    },
    getTotal(valor) {
        return Math.round(valor)
    }
  },
};
</script>

<style scoped>
.badge {
  margin: 2px;
  font-size: 150%;
  background-color:rgb(0, 0, 0) ;

}
label {
  font-weight: 700;
  font-size: 130%;
  
}



</style>
