<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from "axios";
import { store } from "./store.js";

export default {

  data() {
    return{
      store,
    }
  },

  components: {
    AppHeader,
    AppMain,
    AppFooter
  },

  methods: {
    getCard(searchedText){
      // const urlApi = (searchedText=="")?`https://db.ygoprodeck.com/api/v7/cardinfo.php?&num=10&offset=0`: `https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${searchedText}&num=10&offset=0`
      axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?&num=10&offset=0`, {
        params: (searchedText =="") ? {} : {archetype: searchedText}
      })
      .then((response) => {
        console.log(response.data.data);
        this.store.cardsList = response.data.data;
      })
      .catch(function (error) {
        console.log(error);
      })

    }
  },

  created (){
    this.getCard("");
  }
}
</script>

<template>
    <header>
      <AppHeader />
    </header>
  
    <main>
      <AppMain :cards="store.cardsList" @searchCard="getCard" />
    </main>
  
    <footer>
      <AppFooter />
    </footer>
</template>

<style lang="scss">
@use "./styles/general.scss" as *;
@use "bootstrap/scss/bootstrap.scss" as *;

body{
  background-color: #e5af6c;
}
</style>
