<template>
  <cart v-show="isCart" class="mt-10 pa-10" />
  <div class="d-flex flex-wrap justify-space-around mt-16">
    <div v-for="list in lists" class="ma-10" v-show="!isCart">
      <card :list="list" />
    </div>
  </div>
  <v-card max-width="448" class="mx-auto" color="grey-lighten-3">
    <v-layout>
      <v-app-bar
        color="teal-darken-4"
        image="https://picsum.photos/1920/1080?random"
      >
        <template v-slot:image>
          <v-img
            gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.8)"
          ></v-img>
        </template>

        <template v-slot:prepend>
          <v-app-bar-nav-icon></v-app-bar-nav-icon>
        </template>

        <v-app-bar-title>Shopping</v-app-bar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
        <v-btn @:click="isCart = !isCart" icon>
          <v-badge :content="countItem" color="error">
            <v-icon>mdi-cart-outline</v-icon>
          </v-badge>
        </v-btn>
      </v-app-bar>
    </v-layout>
  </v-card>
</template>

<script>
import Card from "../components/Card.vue";
import Cart from "./Cart.vue";
import axios from "axios";

export default {
  name: "Shop",
  data() {
    return {
      lists: [],
      isCart: false,
    };
  },
  mounted() {
    axios
      .get("https://fakestoreapi.com/products")
      .then((response) => (this.lists = response.data));
  },
  computed: {
    countItem() {
      return this.$store.state.counts;
    },
  },
  components: {
    Card,
    Cart,
  },
};
</script>
