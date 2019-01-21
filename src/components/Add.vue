<template>
  <div>
    <NavBar></NavBar>
    <b-container class="bv-example-row pt-5">
      <b-row>
        <b-col>
          <b-form @submit.prevent="onSubmit">
              <b-form-group
                id="exampleInputGroup1"
                label="First name"
                label-for="exampleInput1">
                <b-form-input
                id="exampleInput1"
                type="text"
                v-model="form.firstName"
                required
                placeholder="Enter first name">
                </b-form-input>
              </b-form-group>
              <b-form-group
                id="exampleInputGroup2"
                label="Last name"
                label-for="exampleInput2">
                <b-form-input
                id="exampleInput1"
                type="text"
                v-model="form.lastName"
                required
                placeholder="Enter last name">
                </b-form-input>
            </b-form-group>
              <b-form-group
                id="exampleInputGroup3"
                label="Email"
                label-for="exampleInput3">
                <b-form-input
                id="exampleInput3"
                type="email"
                v-model="form.email"
                required
                placeholder="Enter email">
                </b-form-input>
            </b-form-group>
              <b-form-group
                id="exampleInputGroup4"
                label="Gender"
                label-for="exampleInput4">
                <b-form-input
                id="exampleInput4"
                type="text"
                v-model="form.gender"
                required
                placeholder="Enter gender">
                </b-form-input>
            </b-form-group>
            <b-button type="submit" variant="primary">Go</b-button>
          </b-form>
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
      form: {
          firstName: '',
          lastName: '',
          email: '',
          gender: ''
      },
    }
  },
  methods: {
    onSubmit() {
      this.axios.post('http://104.248.198.169/api/persons', {
            "id": "1005",
            "first_name": this.form.firstName,
            "last_name": this.form.lastName,
            "email": this.form.email,
            "gender": this.form.gender,
            "ip_address": "65.47.33.45"})
      .then(response => {
        console.log(response);
        this.resetValues();
      })
      .catch(error => {
        console.log(error);
      });
    },

    resetValues() {
      Object.keys(this.form).forEach(v => this.form[v] = '');
    }


    // getResults() {
    //   this.axios.get('http://104.248.198.169/api/persons' + '?query=' + this.form.query)
    //   .then(response => {
    //     //console.log(response.data);
    //     this.results = response.data;
    //   })
    //   .catch(error => {
    //     console.log(error);
    //   });
    // }
  }
}
</script>
