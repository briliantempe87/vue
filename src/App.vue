<template>
  <div id="app" class="container mt-5">
    <h1>IDShop</h1>
    <!-- <p class="animate__animated animate__fadeInLeft">Lorem ipsum dolor sit amet consectetur adipisicing elit. Necessitatibus quasi dolores sunt dolorem omnis amet eaque odio! Velit eaque culpa, adipisci molestiae sed nihil, totam quisquam ad ut aspernatur architecto.</p>
    <font-awesome-icon icon="shopping-cart"></font-awesome-icon>
    <price-component :value="4.23">
    </price-component> -->
    <produk-list :products="products" :maximum="maximum"></produk-list>
  </div>
</template>

<script>
// import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome";
// import PriceComponent from "./components/bajing-balap.vue"; 
import ProdukList from "./components/produk-list";

export default {
  name: "app",
  data: function () {
    return {
      maximum:50,
      products:[]
    }
  },
  components: {
    // FontAwesomeIcon,
    // PriceComponent
    ProdukList
  },
  mounted: function() {
        fetch('https://hplussport.com/api/products/order/price')
            .then(response => response.json())
            .then(data => {
                this.products = data;
            });
    },
};
</script>
