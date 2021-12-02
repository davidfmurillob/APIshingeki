<template>
  <!-- <div class="bg-dark text-white">
    
    <div v-for="titan in titanes" v-bind:key="titan">
      <h2>Nombre: {{titan.name}}</h2>
      <h4>Edad: {{titan.Age}}</h4>
      <h5>Alliance: {{titan.alliance}}</h5>
      <h5>Death: {{titan.Death}}</h5>
      <img v-bind:src="titan.img" alt="" />
    </div>
  </div>  -->

  <div class="container-fluid text-white bg-dark">
    <b-row>
      <b-col class="tarjetas col-md-4" v-for="titan in titanes" v-bind:key="titan" >
        <h2>Nombre: {{ titan.name }}</h2>
        <h4>Edad: {{ titan.Age }}</h4>
        <h5>Alliance: {{ titan.alliance }}</h5>
        <h5>Death: {{ titan.Death }}</h5>
        <img v-bind:src="titan.img" alt="" />
      </b-col>
    </b-row>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import axios from "axios";

// import axios from "axios";

@Component({
  components: {},
})
export default class Home extends Vue {
  titanes = [];
  mounted() {
    this.obtenerTitanes();
  }

  obtenerTitanes() {
    axios
      .get("https://my-json-server.typicode.com/Joanutsu/SNK-JSON/SNK")
      .then((response) => {
        this.titanes = response.data;
        console.log(this.titanes);
      })
      .catch(() => {
        alert("No es exitosa");
      })
      .finally();
  }
}
</script>
<style scoped>
.tarjetas{
    border: darkseagreen solid 2px;
    border-radius: 25px;

}
</style>