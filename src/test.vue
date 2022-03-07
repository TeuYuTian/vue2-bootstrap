<template>
  <div id="app">

        ================

    <button class="greenFont" @click="increase"> +1</button>
    <button class="redFont" @click="decrease"> -1</button>
    
    
    <p v-if="showText">This is true!</p>
    <p v-else>This is false!</p>

    <b-btn @click="showText= !showText">Click me to change text.</b-btn>


    <p v-if="showNumber== 1">This is 1.</p>
    <p v-else-if="showNumber== 2">This is 2.</p>
    <p v-else>This is neither one.</p>

    <div v-for="i,index in products" :key="i.name" :index="index">
      <p :style="'color:'+i.fontColor">{{index+1}}. Name: {{i.name}}</p>
      <p>{{i.quantity}} pcs</p>
      <img :src="i.image"> Image Source: {{i.image}}
      <p>Price: RM{{products[index].price}}</p>

    </div>

    <p>Original message: "{{ message }}"</p>
    <p>Computed reversed message: "{{ reversedMessage }}"</p>
    <p>Computed Caps: "{{ allCapsMessage }}"</p>


    <p>Original Total: {{counter}}</p>
    <p>Discounted Total: {{totalPrice}}</p>

    <button class="greenFont" @click="increase"> +1</button>
    <button class="redFont" @click="decrease"> -1</button>
    <br>
    <button class="greenFont" @click="increase5"> +5</button>
    <button class="redFont" @click="decrease5"> -5</button>






  </div>
</template>

<script>
export default {
  data(){
    return{
      // message: "Please enter your details below",

          // calcTotal(){
    //   let total = 0;

    //   for (let i = 0 ; i < this.products.length; i++){
    //   total += this.products[i].quantity*this.product[i].price
    //   }
    //   return total;
    // },

    // calcDiscount(){
    //   if(this.totalsales >60) {
    //     this.discountPct =0.15;
    // }else if (this.totalSales >40){
    //   this.discountPct =0.1;
    // } else {
    //   this.discountPct =0;
    // }
    //   return this.totalSales * (1 - this.discountPct);

    // },
    //  calcShippingFees(){
    //    let fees = 20;
    //    if (this.pickupArea == 0) {
    //      fees=15;
    //    } else if (this.pickupArea == 5){
    //      fees=25;
    //    }
    //    return fees;
    //  },
    
      name: "",
      addr: "",
      email: "",
      tel: "",
      image1: "apple.jpg",
      image2: "orange.jpg",
      image3: "strawberry.jpg",
      url1: "https://apple.com",
      url2: "https://orange.com",
      url3: "https://abc.com",
      web1: "Fruit Company",
      web2: "Orange Company",
      web3: "Another Fruit Company",
      counter: 0,
      message: "hello world from vue js",
      showText: true,
      showNumber: 10,
      products: [
        {
          name: "Apple",
          quantity: 10,
          price: 10,
          stock: 0,
          image: "apple.jpg",
          url: "https://www.google.com",
          fontColor: "red"
        },
        {
          name: "Orange",
          quantity: 0,
          price: 12,
          stock: 0,
          image: "orange.jpg",
          url: "https://www.facebook.com",
          fontColor: "yellow"
        },
        {
          name: "Strawberry",
          quantity: 5,
          price: 9,
          stock: 0,
          image: "strawberry.jpg",
          url: "https://www.discord.com",
          fontColor: "green"
        },
        {
          name: "Strawberry 2",
          quantity: 7,
          price: 7,
          stock: 0,
          image: "strawberry.jpg",
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
  methods:{
    increase() {
      this.counter = this.counter + 1;
    },
    decrease() {
      this.counter = this.counter - 1;
    },
    increase5() {
      this.counter = this.counter + 5;
    },
    decrease5() {
      this.counter = this.counter - 5;
    },
  },
  computed:{
    reversedMessage() {
      return this.message.split('').reverse().join('') 
    },
    allCapsMessage(){
      return this.message.toUpperCase()
    },
    totalPrice(){
      let discount=0.15 
      return this.counter*discount 
    }
  }
}
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

