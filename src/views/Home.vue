<template>
  <div>
    <NavBar></NavBar>
    <b-container class="bv-example-row pt-5">
      <b-row>
        <b-col>
          <b-form-group
            id="exampleInputGroup1"
            label="Search for persons:"
            label-for="exampleInput1">
            <b-form-input
              id="exampleInput1"
              type="email"
              v-model="form.query"
              @input="getResults"
              required
              placeholder="Enter search query">
            </b-form-input>
          </b-form-group>
        </b-col>
      </b-row>
    </b-container>
    <b-container class="pt-5">
      <b-row>
        <b-col>
          <p>{{results.length}} Results</p>
          <b-table hover :items="results" :fields="columns"></b-table>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>

import NavBar from '../components/NavBar';
export default {
  name: 'home',
  components: {
    NavBar
  },
  data() {
    return {
      query: '',
      results: [],
      columns: ['first_name','last_name','email','gender','ip_address'],
      form: {
        query: '',
      },
    }
  },
  methods: {

    getResults() {
      this.axios.get('http://104.248.198.169/api/persons' + '?query=' + this.form.query)
      .then(response => {
        //console.log(response.data);
        this.results = response.data;
      })
      .catch(error => {
        console.log(error);
      });
    }
  }
}
</script>
