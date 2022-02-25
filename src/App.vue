<template>
  <div id="app">
    <h2 class="greenFont">My first ever Vue Tutorial</h2>
      <h4 class="blueFont">{{ message }}</h4>
      Name:<input type="text" v-model="name"/> <br> 
      Addr:<input type="text" v-model="addr"/> <br> 
      Email:<input type="text" v-model="email"/> <br> 
      Tel:<input type="text" v-model="tel"/>  <br><br>
      <h2>Name : {{ name }}</h2>
      <h3>Addr :{{ addr }}</h3>
      <h3>Email: {{ email }}</h3>
      <h3>Tel: {{ tel }}</h3>
    <button class="greenFont" @click="increase"> +1</button>
    <button class="redFont" @click="decrease"> -1</button>
    
    
    <h1>Conditional Rendering</h1>
    <p v-if="showText">This is true!</p>
    <p v-else>This is false!</p>

    <b-btn @click="showText= !showText">Click me to change text.</b-btn>

    ================

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

</style>