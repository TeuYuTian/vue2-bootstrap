<template>
  <div id="app">
    <h2 class="greenFont">My first ever Vue Tutorial</h2>

    <h4 class="blueFont">{{ message }}</h4>

    Name:<input type="text" v-model="name" /> <br>
    Addr:<input type="text" v-model="addr"/> <br>
    Email:<input type="text" v-model="email"/> <br>
    Tel:<input type="text" v-model="tel"/> <br>


    <h2>Name: {{name}}</h2>
    <h2>Addr: {{addr}}</h2>
    <h2>Email: {{email}}</h2>
    <h2>Tel: {{tel}}</h2>

    <img v-bind:src="image1">
    <img :src="image2">
    <img :src="image3">

    <h3 class="redbg"><a :href="url1">{{web1}}</a></h3>
    <h3><a :href="url2">{{web2}}</a></h3>
    <h3><a :href="url3">{{web3}}</a></h3> <hr>

    <button class="greenFont" @click="increase"> Increase</button>
    <button class="blueFont" v-on:click="decrease"> Decrease</button> <br>
    <button class="greenFont" @click="increasefive"> Increase5</button>
    <button class="redFont" @click="decreasefive"> Decrease5</button>

    <h2>{{counter}}</h2>
    

  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      message: "Please enter your details below",
      name: "",
      addr: "",
      email: "",
      tel: "",
      image1: "apple.jpg",
      image2: "orange.jpg",
      image3: "strawberry.jpg",
      url1: "http://apple.com",
      url2: "http://orange.com",
      url3: "http://abc.com",
      web1: "Fruit Company",
      web2: "Orange Company",
      web3: "ABC Company",
      counter:0,
    };
  },
  methods: {
    increase(){
      this.counter= this.counter +1;
    },
      decrease(){
      this.counter= this.counter -1;
    },
    increasefive(){
      this.counter= this.counter +5;
    },
      decreasefive(){
      this.counter= this.counter -5;
    }
  },
  computed: {},
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}

.blueFont {
  color: blue;
}

.greenFont {
  color: green;
  font-size: 30px;
}

.redFont {
  color: red;
  font-size: 30px;
}

.redbg {
  background: red;
}
</style>
