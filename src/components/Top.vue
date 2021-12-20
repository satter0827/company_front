<template>
  <div class="alert alert-info">
    <p>企業名で検索</p>
    <input class= "form-control" type="text" v-model="input">  
    <button class="btn btn-info mt-2" v-on:click="doAction">Click</button>

    <tbody>
      <tr v-for="company in companies" v-bind:key="company.id">
        <th>{{ item.company_id }}</th>
        <td>{{ item.name }}</td>
        <td>{{ item.url }}</td>
      </tr>
    </tbody>

    <p>input = {{ keyword }}</p>
  </div>
</template>

<script>
import axios from 'axios'
//import { reactive, onMounted } from 'vue'

let url = "http://127.0.0.1:8000/main_api/company/"

export default({
  name: 'search',
  data() {
    return {
      keyword: "",
      input: "",
      companies: null,
    }
  },
  methods: {
    doAction() {
      this.keyword = this.input
    },
    getAllCompany() {
      axios.get(url).then(response => {
        this.company = response.data.results
      })
    }
  },

})
</script>
