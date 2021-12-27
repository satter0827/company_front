<template>
  <div id="search">
    <div class="alert alert-info">
      <p>企業名で検索</p>
      <input class= "form-control" type="text" v-model="searchword">  

      <div class="center-block" v-for="company in companies" v-bind:key="company.company_id">
        <td><a v-bind:href="company.url">{{ company.name }}</a></td>
      </div>

    </div>
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
