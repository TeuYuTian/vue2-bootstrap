<template>
  <div id="app">
    <h1>Conditional Rendering</h1>

    <p v-if="showText">This is true!</p>
    <p v-else>This is false!</p>

    <b-btn @click="showText= !showText">Click me to change text.</b-btn>
    


    <p v-if="showNumber==1">This 1</p>
    <p v-else-if="showNumber==2">This 2</p>
    <p v-else>This is neither one.</p>

    <div v-for="i,index in products" :key="i.name" :index="index">
      <p :style="'color:'+ i.fontColor">{{index+1}} Name: {{i.name}}</p>
      <p>{{i.quantity}} pcs</p>
      <img :src="i.image">Image Source: {{i.image}}
      <p>Price: RM{{products[index].price}}</p>

      <p>Original message: "{{message}}"</p>
      <p>Comuted reversed message: "{{reveredMessage}}"</p>
      <p>Comuted Caps: "{{allCapsMessage}}"</p>

      <p>Original Total: {{counter}}</p>
      <p>Discounted Total: {{totalPrice}}</p>
      
      <button class="greenFont" @click="increase"> +1</button>
      <button class="redFont" @click="decrease"> -1</button>
      <br>
      <button class="greenFont" @click="increase5"> +5</button>
      <button class="redFont" @click="decrease5"> -5</button>



    </div>

    view and components
    

    </div>
</template>

<script>
export default {
  data(){
    return{
      message: "hello",
      showText: true,
      showNumber: 10,

      products: [
        {
          name: "Apple",
          quantity: 10,
          price: 10,
          stock: 0,
          image: "apple.jpg",
          url: "https://www.google.com/",
          fontColor: "red"
        },
        {
          name: "Orange",
          quantity: 0,
          price: 12,
          stock: 0,
          image: "orange.jpg",
          url: "https://www.facebook.com/",
          fontColor: "yellow"


        },
        {
          name: "Strawberry",
          quantity: 5,
          price: 9,
          stock: 0,
          image: "strawberry.jpeg",
          url: "https://www.discord.com/",
          fontColor: "green"

        },
        {
          name: "Strawberry 2",
          quantity: 7,
          price: 7,
          stock: 0,
          image: "strawberry.jpeg",
          fontColor: "green"

        },
        {
          name: "Orange 2",
          quantity: 0,
          price: 13,
          stock: 0,
          image: "orange.jpg",
          fontColor: "yellow"

        },
        {
          name: "Apple 2",
          quantity: 0,
          price: 11,
          stock: 0,
          image: "apple.jpg",
          fontColor: "red"

        },
      ],


    }
  },

  methods: {

  },

  computed:{
    reversedMessage(){
      return this.message.split('').reverse().join('')
    },
  }


}
</script>

<style>

</style>