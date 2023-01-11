<script>
import CardElement from "./CardElement.vue";
import { store } from "../store.js";

export default{
  components: {
    CardElement,
  },

  props: [
    `cards`
  ],

  data() {
    return{
      store,
    }
  },

}
</script>

<template>
  <div class="main-container">
    <section class="cards-found">
      <h4>Found ...</h4>
    </section>
    <section class="grid-cards">
      <CardElement v-for="cardElement in cards" 
      :imagePath="cardElement.card_images[0].image_url"
      :nameEl="cardElement.name"
      />
      <!-- <p v-for="cardElement in cards">
        {{ cardElement.card_images[0].image_url }}
        {{ cardElement.name }}
      </p> -->
    </section>
  </div>
</template>

<style lang="scss" scoped>
  .main-container{
    width: 90%;
    height: 1000px;
    margin: 5rem auto;
    background-color: white;
    // border-radius: 20px;
    padding: 3.5rem;
    .cards-found{
      width: 100%;
      background-color: #212529;
      padding: 1.5rem 1rem;
      color: white;
    }
  }
</style>
