<template>
    <nav class="navbar navbar-light bg-light">
            <div class="navbar-text ms-auto d-flex">
                <button class="btn btn-sm btn-outline-success" @click="$emit('toggle')">
                    <font-awesome-icon icon="dollar-sign"></font-awesome-icon>
                </button>
                <div class="ms-2 dropdown" v-if="cart.length > 0">
                    <button class="btn btn-success btn-sm dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                        <b>cart:</b>
                        <span class="badge bg-success">{{ cartQty }}</span>
                        <font-awesome-icon icon="shopping-cart"></font-awesome-icon>
                        <price :value="Number(cartTotal)"></price>
                    </button>
                    <!-- <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
                        <li v-for="(item, index) in cart" :key="index">
                            <a class="dropdown-item" href="#">
                                <span class="badge badge-pill badge-warning align-text-top mr-1">
                                    {{ item.qty }}
                                </span>
                                {{ item.name }}
                                <b>{{ item.price | currencyFormat }}</b>
                            </a>
                        </li>
                      </ul> -->
                    <div class="dropdown-menu dropdown-menu-end" aria-labelledby="dropdownCart">
                        <div v-for="(item, index) in cart" :key="index">
                            <div class="dropdown-item-text text-nowrap text-right">
                                <span class="badge bg-warning align-text-top mr-1">
                                    {{ item.qty }}
                                </span>
                                {{ item.product.name }}
                               <b>{{ item.qty * item.product.price | currencyFormat }}</b>
                                <a href="#" class="badge badge-danger text-white" @click.stop="$emit('delete', index)">-</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </nav>
</template>

<script>
import Price from "./PriceItem.vue";
import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome";

export default {
    name: "navbar-item",
    components: {
        Price,
        FontAwesomeIcon
    },
    props: ["cart", "cartQty", "cartTotal"],
    filters: {
        currencyFormat: function (value) {
            return 'Rp' + Number.parseFloat(value).toFixed(2);
        }
    },
}
</script>