<template>
<nav class="navbar navbar-light fixed-top">
            <div class="navbar-text ml-auto d-flex">
                <button class="btn btn-sm btn-outline-success" @click="$emit('toggle-slide')">
                    <font-awesome-icon icon="dollar-sign"></font-awesome-icon>
                </button>
                <div class="ml-2 dropdown" v-if="cart.length > 0">
                    <button class="btn btn-success btn-sm dropdown-toggle" id="dropdownCart123" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                        
                        <span class="badge badge-pill badge-success">{{ cartQty }}</span>
                        <font-awesome-icon icon="shopping-cart"></font-awesome-icon> 
                        <price :value="Number(cartTotal)"></price>

                    </button>
                    <div class="dropdown-menu dropdown-menu-right" aria-labelledby="dropdownCart">
                        <div v-for="(item, index) in cart" :key="index">
                            <div class="dropdown-item-text text-nowrap text-right">
                                <span class="badge badge-pill badge-warning align-text-top mr-1">
                                    {{ item.qty }}
                                </span>

                                {{ item.product.name }}
                                <b>{{ item.product.price | currencyFormat }}</b>
                                <a href="#" class="badge badge-danger text-white" @click.stop="$emit('delete-item', index )">-</a>
                            </div>
                        </div>
                        <router-link class="btn btn-sm btn-outline-info text-dark mr-2 float-right" to="/checkout">checkout</router-link>
                    </div>
                </div>
            </div>
        </nav>
</template>

<script>

import Price from "./PriceComponent"
import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome";

export default {
    name:"navbar-component",
    components: {
    FontAwesomeIcon,
    Price
  },
    props: ['cart', 'cartQty', 'cartTotal'],
    filters: {
        currencyFormat: function (value) {
            return 'Rp' + Number.parseFloat(value).toFixed(2);
        }
}
}
</script>import PriceComponentVue from "./PriceComponent.vue";
