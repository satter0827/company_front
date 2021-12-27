<template>
  <v-app>
    <v-main>
      <Header/>

      <div class="container">
        <Top />
      </div>

      <div class="container">
        <Footer/>
      </div>
    </v-main>
  </v-app>
</template>

<script>
import Top from './components/Top.vue'
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";

export default {
  name: 'App',

  components: {
    Top,
    Header,
    Footer,
  },

  data: () => ({
    //
  }),
};
</script>
