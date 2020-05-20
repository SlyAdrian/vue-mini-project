<template>

  <div id="app">
     <head>
      <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    </head>
    <div class="jumbotron">
      <h1 class="display-4 font-weight-bold text-center">Unit Converter</h1>
      <p class="lead"> This application aims at converting units that the user enters.</p>
      <hr class="my-2">
      <p class="lead">User can add conversion units by giving them a name and a base multiplier.</p>
    </div>

    <div class="container">
      <div class="jumbotron col-12">
        <div class="row">
          Enter Unit : 
          <input type="text" v-model="unit"> 
        </div>
        <div class="row">
          <p class="my-3">The unit entered is {{ unit }}.</p>
        </div>  
      </div>
      <div class="jumbotron">
        <h2 class="text-center">Add new Unit</h2>
        <div class="row my-5 ">           
          <new-unit-form @added="addUnit($event)"></new-unit-form>
        </div>
        <ul>
          <li v-for="unitC in conversions" :key="unitC">
            1 {{unit}} = {{ unitC.multiplier }} {{unitC.name}}
          </li>
        </ul>
        
      </div>
      <div class = "jumbotron" v-if="conversions.length >0">
        <h1>Conversions</h1>
        <label>Enter the value you want to convert : </label>
        <input type="text" v-model="converted">
        <button v-on:click="convert()"> Convert </button>

          <ul v-if="valueE==true">
            <!-- <my-component></my-component> -->
            <li v-for="unitC in conversions" :key="unitC" >
              {{ converted }} {{ unit }} = calculate(5,2) {{ unitC.name }}
            </li>
          </ul>
        <!-- v-model="newUnit.value" -->
        <!-- {{ unitC.value }} {{ unit }} = ({{ unitC.value }} * {{ unitC.multiplier }}) {{ unitC.name }} -->
      </div>
    </div>    
  </div>

</template>

<script>

import NewUnitForm from "./NewUnitForm.vue";
/* import myComponent from "./myComponent.vue"; */

export default {
  name: 'App',
  components: { NewUnitForm },
  data() {
    return {
        unit: "EUR",
        converted : "",
        conversions: [],
        valueE: Boolean,
    };
  },
  methods: {
    addUnit(newUnit) {
      this.conversions.push(newUnit)
      this.valueE = false
    },
    convert() {
      this.valueE = true
    },
    calculate(arg1, arg2) {
      return arg1 * arg2
    }
  },
}
</script>

<style>
#app {
/*   font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50; */
  margin-top: 60px;
}
</style>
