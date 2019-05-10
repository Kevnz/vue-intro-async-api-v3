<template>
  <div class="home">
    <ShoppingCart v-bind:cart="cart"/>
    <div id="app">
      <h1>
        <img class="logo" alt="Vue logo" src="../assets/logo.png">The Vue.js Shop
      </h1>
      <div id="nav">
        <router-link to="/">Home</router-link>|
        <router-link to="/checkout">Checkout</router-link>|
        <router-link to="/about">About</router-link>
      </div>
      <ProductList v-bind:products="products" v-on:add-to-cart="addToCart"></ProductList>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Welcome from "@/components/Welcome.vue";
import ProductList from "@/components/ProductList.vue";
import ShoppingCart from "@/components/ShoppingCart.vue";

export default {
  name: "home",
  components: {
    ProductList,
    Welcome,
    ShoppingCart
  },
  data() {
    console.info("Data in home");
    return {
      cart: window.cart || {
        total: 0,
        items: [],
        cost: 0
      },
      products: [
        {
          id: "d5637ec1-3478-4f0b-9cbd-ac74ef591ad4",
          name: "Refined Soft Chicken",
          price: "983.00",
          category: "Shoes",
          description: "Refined Frozen. Reactive asymmetric capacity.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}a`
        },
        {
          id: "8d0d6346-de4c-443e-8c85-10f66d13354d",
          name: "Rustic Concrete Pizza",
          price: "960.00",
          category: "Games",
          description: "Licensed Rubber. Ameliorated demand-driven attitude.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}b`
        },
        {
          id: "8ded54bb-ed74-4a83-bf63-655915413da7",
          name: "Unbranded Rubber Keyboard",
          price: "831.00",
          category: "Baby",
          description: "Intelligent Cotton. Cloned next generation encoding.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}c`
        },
        {
          id: "58b4d888-b25d-4308-8811-44b0e9a58694",
          name: "Licensed Frozen Chair",
          price: "796.00",
          category: "Sports",
          description: "Rustic Frozen. Polarised mobile emulation.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}d`
        },
        {
          id: "024f0048-3c50-4000-9cf8-e7bd87265bf5",
          name: "Unbranded Wooden Tuna",
          price: "450.00",
          category: "Electronics",
          description:
            "Awesome Metal. Ameliorated zero administration open system.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}e`
        },
        {
          id: "0f84caed-67d5-434c-b05a-13eb0b926598",
          name: "Fantastic Concrete Sausages",
          price: "433.00",
          category: "Beauty",
          description: "Ergonomic Wooden. Ergonomic eco-centric archive.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}f`
        },
        {
          id: "092cd0cf-3f6b-4aba-979b-29d84f0caa52",
          name: "Rustic Rubber Ball",
          price: "735.00",
          category: "Automotive",
          description: "Tasty Rubber. Exclusive clear-thinking extranet.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}g`
        },
        {
          id: "235b6497-f16b-41bc-b369-af702fcae7c1",
          name: "Small Granite Shoes",
          price: "87.00",
          category: "Electronics",
          description: "Licensed Fresh. Profound composite leverage.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}h`
        },
        {
          id: "ea949e01-bd35-418d-9541-29c4c75e8250",
          name: "Unbranded Wooden Pizza",
          price: "387.00",
          category: "Shoes",
          description:
            "Intelligent Concrete. Universal content-based projection.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}i`
        },
        {
          id: "808d68c1-bbe8-4cfb-a869-9e0221b475e0",
          name: "Generic Metal Table",
          price: "965.00",
          category: "Baby",
          description: "Tasty Steel. Sharable bottom-line extranet.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}j`
        },
        {
          id: "61c4c7e0-d57e-4db4-b8c4-6157c572518f",
          name: "Unbranded Rubber Chair",
          price: "176.00",
          category: "Jewelery",
          description: "Handcrafted Metal. Open-source local initiative.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}k`
        },
        {
          id: "0168603b-8a10-4c50-99c7-fad9798879ff",
          name: "Refined Cotton Mouse",
          price: "773.00",
          category: "Games",
          description: "Sleek Soft. Managed discrete process improvement.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}l`
        },
        {
          id: "9e82d3e0-9e70-4676-8adb-3d75a5a1e6f8",
          name: "Gorgeous Soft Bacon",
          price: "848.00",
          category: "Jewelery",
          description: "Ergonomic Granite. Synchronised bifurcated time-frame.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}m`
        },
        {
          id: "de5c4a39-35cb-44b2-b5c2-6eab2dae8401",
          name: "Rustic Granite Mouse",
          price: "430.00",
          category: "Outdoors",
          description: "Fantastic Cotton. Integrated directional workforce.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}n`
        },
        {
          id: "dd8e7010-9c0c-4938-9097-9726c9c2f865",
          name: "Gorgeous Steel Towels",
          price: "350.00",
          category: "Tools",
          description:
            "Generic Concrete. Intuitive user-facing process improvement.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}o`
        },
        {
          id: "c0b2ffb9-b0f3-489a-9f08-b2de1aa575d5",
          name: "Handcrafted Fresh Sausages",
          price: "232.00",
          category: "Grocery",
          description: "Incredible Fresh. Adaptive incremental projection.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}p`
        },
        {
          id: "eb5a6638-6d90-427d-b741-50d721234d95",
          name: "Intelligent Rubber Computer",
          price: "359.00",
          category: "Computers",
          description:
            "Gorgeous Concrete. Re-contextualized attitude-oriented system engine.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}q`
        },
        {
          id: "11b51b50-f355-4258-ae30-b43a81e00650",
          name: "Gorgeous Plastic Bike",
          price: "997.00",
          category: "Outdoors",
          description: "Rustic Cotton. Focused impactful monitoring.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}r`
        },
        {
          id: "931bbf8b-ccf8-4fe9-99b4-2f2d17bf7cdc",
          name: "Gorgeous Wooden Hat",
          price: "450.00",
          category: "Beauty",
          description: "Sleek Wooden. Multi-lateral asymmetric groupware.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}s`
        },
        {
          id: "37efef0b-88ee-4d4b-9964-be91001b969c",
          name: "Practical Rubber Shirt",
          price: "257.00",
          category: "Outdoors",
          description: "Small Metal. Streamlined intangible neural-net.",
          image: `https://lorempixel.com/320/240?x=${Date.now()}t`
        }
      ]
    };
  },
  methods: {
    addToCart(product) {
      console.log("add to cart", this.cart.items);
      if (this.cart.items.filter(i => i.id === product.id).length === 0) {
        this.cart.items.push({ ...product, quantity: 1 });
      } else {
        this.cart.items.filter(i => product.id === i.id)[0].quantity++;
      }
      const q = this.cart.items.reduce((quantity, entry) => {
        return quantity + entry.quantity;
      }, 0);
      const cost = this.cart.items.reduce((amount, entry) => {
        return amount + entry.quantity * entry.price;
      }, 0);
      this.cart.total = q;
      this.cart.cost = cost;

      if (!window.cart) window.cart = {};
      window.cart = this.cart;
    }
  }
};
</script>
