<script>
import CardElement from "./CardElement.vue";
import AppLoader from "./AppLoader.vue";
import { store } from "../store.js";

export default{
  components: {
    CardElement,
    AppLoader
  },

  props: [
    `cards`,
  ],

  data() {
    return{
      store,
      isLoading : true,
      searchString : "",
      archetypeList: ['Alien', 'Laval', 'Vylon', 'Inzektor', 'Umi', 'Gusto']
    }
  },

  methods: {
    stopLoader() {
      this.isLoading = false;
    }
  },

  created() {
    setTimeout(this.stopLoader, 2000);
  }

}
</script>

<template>
  <div class="main-container">
    <section class="select-part">
      <select class="archetype-selector" name="archetype-selector" v-model="searchString" @change="$emit(`searchCard`, searchString)">
        <option v-for="archetypeCard in archetypeList">
        {{ archetypeCard }}
        </option>
      </select>
    </section>
    <section class="cards-found">
      <h4>Found {{ cards.length }} cards</h4>
    </section>
    <section class="grid-cards row">
      <AppLoader v-if="isLoading" />
      <CardElement v-else v-for="cardElement in cards" 
      :imagePath="cardElement.card_images[0].image_url"
      :nameEl="cardElement.name"
      :archetype="cardElement.archetype"
      />
    </section>
  </div>
</template>

<style lang="scss" scoped>
  .main-container{
    width: 90%;
    margin: 5rem auto;
    background-color: white;
    border-radius: 20px;
    padding: 3.5rem;
    .select-part{
      padding-bottom: 1.5rem;
      .archetype-selector{
        width: 150px;
        height: 2rem;
        font-size: 1rem;
      }
    }
    .cards-found{
      width: 100%;
      background-color: #212529;
      padding: 1.5rem 1rem;
      color: white;
    }
    .grid-cards{
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
    }
  }
</style>
