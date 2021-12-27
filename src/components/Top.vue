<template>
  <div id="search">
    <div class="alert alert-info">
      <p>企業名で検索</p>
      <input class= "form-control" type="text" v-model="input">  

        <tbody>
          <tr v-for="company in companies" v-bind:key="company.company_id">
            <td>{{ company.name }}</td>
            <td>{{ company.url }}</td>
          </tr>
        </tbody>
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
      keyword: "",
      input: "",
      companies: [],
      counter: 0
    }
  },
  mounted() {
    this.getCompany();
  },
  methods: {
    doAction() {
      this.keyword = this.input
    },
    async getCompany() {
      this.counter++
      await axios.get(url).then((response) => {
        this.companies = response.data["results"]
      })
    }
  },

})
</script>
