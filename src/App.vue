<template>
  <div id="app">

    <b-row>
      <div v-for="i,index in products" :key="i.name" :index="index">
        <b-col>
          <b-card class="mt-4">
            {{i.name}}
            <br/>
            <img :src="i.image" width="100%"/>
            <br>

            Price: {{i.price}}
            <br>

            <b-button class="mr-2" variant ="success" size="sm" @click="increase5(i)" > +5 </b-button>
            <b-button variant="success" size="sm" @click="increase(i)"> + </b-button>

            {{i.quantity}}

            <b-button class="mr-2" variant ="danger" size="sm" @click="decrease(i)"> - </b-button>
            <b-button variant="danger" size="sm" @click="decrease5(i)"> -5 </b-button>
            <br/>
            Subtotal: RM{{i.quantity*i.price}}
          </b-card>
        </b-col>    
      </div>
    </b-row>

    <hr>


Item Qty Price Subtotal
<div v-for="i,index in products" :key="i.name" :index="index">
  <div v-if="i.quantity > 0" >
    {{i.name}} {{i.quantity}}
  </div>
</div>

total sales: {{calcTotal}} <br>

total discount amt: {{calcDiscount}} <br>
discount given in % : {{discountAmt * 100 }}% <br>

** if sales above 100, give free shipping, else fee = 10 <br>

<b-row>
  <b-col cols="4">
    Delivery Area:
    <b-form-select
    v-model="pickupArea"
    :options="areaOptions"
    ></b-form-select>
  </b-col>
</b-row>

Shipping Fees: {{calcShippingFees}} <br>
Grand Total: {{calcTotal-calcDiscount+calcShippingFees}}<br>

  </div>

</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      name: "",
      mobile: "",
      email: "",
      quantity: 0,
      totalSales: 0,
      discountPct: 0,
      pickupArea: 0,
      areaOptions: [
        { value: "0", text: "Mont Kiara" },
        { value: "1", text: "Cheras" },
        { value: "2", text: "Puchong" },
        { value: "3", text: "Kepong" },
        { value: "4", text: "Others" },
      ],
      products: [
        {
          name: "Apple",
          quantity: 0,
          price: 10,
          stock: 0,
          image: "apple.jpg",
        },
        {
          name: "Orange",
          quantity: 0,
          price: 12,
          stock: 0,
          image: "orange.jpg",
        },
        {
          name: "Strawberry",
          quantity: 0,
          price: 9,
          stock: 0,
          image: "strawberry.jpg",
        },
        {
          name: "Strawberry 2",
          quantity: 0,
          price: 7,
          stock: 0,
          image: "strawberry.jpg",
        },
        {
          name: "Orange 2",
          quantity: 0,
          price: 13,
          stock: 0,
          image: "orange.jpg",
        },
        {
          name: "Apple 2",
          quantity: 0,
          price: 11,
          stock: 0,
          image: "apple.jpg",
        },
      ],
    };
  },


  methods: {
    increase(i){
      return (i.quantity = i.quantity + 1);

    },
    decrease(i){
      return (i.quantity = i.quantity - 1);
    },
    increase5(i){
      return (i.quantity = i.quantity + 5);
    },
    decrease5(i){
      return (i.quantity = i.quantity - 5);
    },
  },

   computed: {
    calcTotal() {
      let total = 0;
      for (let i = 0; i < this.products.length; i++) {
        total += this.products[i].quantity * this.products[i].price;
      }
    //   this.totalSales = total;
      return total;
    },

discountAmt() {

      let discountPct = 0;

      // this.discountAmt = discountPct;

      if (this.calcTotal > 100) {
        discountPct = 0.15;
      } else if (this.calcTotal > 40) {
        discountPct = 0.1;
      } else {
        discountPct = 0;
      }
      return discountPct;
    },

        calcDiscount() {
      return (this.calcTotal * this.discountAmt);
    },


    calcShippingFees() {
      let fees = 20;
      if (this.pickupArea == 0) {
        fees = 15;
      } else if (this.pickupArea == 4) {
        fees = 25;
      }
      return fees;
    },
  },





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



