<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from "axios";

export default {

  data() {
    return{
      cardsList: [],
    }
  },

  components: {
    AppHeader,
    AppMain,
    AppFooter
  },

  methods: {
    getCard(){

      axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0`, {
        params: {
        }
      })
      .then((response) => {
        console.log(response.data.data);
        this.cardsList = response.data.data;
      })
      .catch(function (error) {
        console.log(error);
      })

    }
  },

  created (){
    this.getCard();
  }
}
</script>

<template>
  <header>
    <AppHeader />
  </header>

  <main>
    <AppMain :cards="cardsList" />
  </main>

  <footer>
    <AppFooter />
  </footer>
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
</style>
