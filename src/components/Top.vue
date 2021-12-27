<template>
  <div id="search">
    <div class="alert alert-info">
      <p>企業名で検索</p>
      <input class= "form-control" type="text" v-model="searchword">  
    </div>

    <v-card class="mt-4 mb-4 pa-3">
      <v-layout row wrap>
        <v-flex xs4 v-for="company in companies" v-bind:key="company.company_id">
          <v-card class="grey lighten-3 ma-2">
            <v-card-text><a v-bind:href="company.url">{{ company.name }}</a></v-card-text>
            <v-card-text>{{ company.business_information }}</v-card-text>
            <link-prevue v-bind:href="company.url"></link-prevue>
          </v-card>
        </v-flex>
      </v-layout>
    </v-card>
  </div>
</template>

<script>
import axios from 'axios'

let url = "https://company-api-001.herokuapp.com/main_api/company/?format=json"

export default({
  name: 'search',
  data() {
    return {
      searchword: "",
      companies: [],
    }
  },
  mounted() {
    this.getCompany();
  },
  methods: {
    async getCompany() {
      this.counter++
      await axios.get(url).then((response) => {
        this.companies = response.data["results"]
      })
    }
  },

})
</script>
