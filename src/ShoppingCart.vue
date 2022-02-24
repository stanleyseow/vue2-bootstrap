<template>
  <div id="app">
    <b-row>
      <div v-for="item in products" :key="item">
        <b-col>
          <b-card>
            {{ item.name }}
            <br />

            <img :src="item.image" width="100%" />
            <br />
            Price: {{ item.price }}
            <br />
            <b-button variant="success" size="sm" v-on:click="increase5(item)">
              5+
            </b-button>
            <b-button variant="success" size="sm" v-on:click="increase(item)">
              +
            </b-button>
            {{ item.quantity }}
            <b-button variant="danger" size="sm" v-on:click="decrease(item)">
              -
            </b-button>
            <b-button variant="danger" size="sm" v-on:click="decrease5(item)">
              -5
            </b-button>

            <br />
            Subtotal: {{ item.quantity * item.price }}
          </b-card>
        </b-col>
      </div>
    </b-row>

    <hr />

    Item Qty Price Subtotal ==== === ===== ========
    <div v-for="item in products" :key="item">
      <div v-if="item.quantity > 0">
        {{ item.name }}
      </div>
    </div>

    total sales : {{ calcTotal }} <br />

    <!-- 
    if total more than 40, give 10% discount
    if total more than 60, give 15% discount 

    display discount % given  
    -->

    total discount (amt) : {{ calcDiscount }} <br />
    discount given in % : {{ discountPct * 100 }}% <br />

    *** if sales above 80, give free shipping, else fee is 10 <br />
    shipping fees : <br />

    <b-row>
      <b-col cols="4">
        Delivery Area :
        <b-form-select
          v-model="pickupArea"
          :options="areaOptions"
        ></b-form-select>
      </b-col>
    </b-row>
    Shipping Fees: {{ calcShippingFees }} <br />
    Grand Total : <br />
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
    increase(item) {
      return item.quantity++;
    },
    decrease(item) {
      return item.quantity--;
    },
    increase5(item) {
      return (item.quantity = item.quantity + 5);
    },
    decrease5(item) {
      return (item.quantity = item.quantity - 5);
    },
  },
  computed: {
    calcTotal() {
      let total = 0;
      for (let i = 0; i < this.products.length; i++) {
        total += this.products[i].quantity * this.products[i].price;
      }
      this.totalSales = total;
      return total;
    },

    calcDiscount() {
      if (this.totalSales > 60) {
        this.discountPct = 0.15;
      } else if (this.totalSales > 40) {
        this.discountPct = 0.1;
      } else {
        this.discountPct = 0;
      }

      return this.totalSales * (1 - this.discountPct);
    },
    calcShippingFees() {
      let fees = 20;
      if (this.pickupArea == 0) {
        fees = 15;
      } else if (this.pickupArea == 5) {
        fees = 25;
      }
      return fees;
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}
.font30 {
  font-size: 30px;
}
.font20 {
  font-size: 10px;
}
.purple {
  color: purple;
}
.bold {
  font-weight: bold;
}
.bg-red {
  background: red;
}

.bg-cyan {
  background: cyan;
}
</style>
