
<template>

  <div>
    <div>
      <div class="form-group">
        <label>Name</label>
        <q-input
          v-model="form.name"
          outlined
          dense
          label="Enter name"
        />
        <small class="form-text text-muted">Type your name!</small>
      </div>
      <div class="form-group">
        <label>Age</label>
        <q-input
          outlined
          dense
          v-model.number="form.age"
          class="form-control"
          placeholder="Enter age"
        />
        <small class="form-text text-muted">Enter the number It can't be string !</small>
      </div>

      <div class="form-group">
        <label>Gender</label>
        <q-input
          outlined
          dense
          v-model="form.gender"
          class="form-control"
          placeholder="Enter gender"
        />
        <small class="form-text text-muted">the value M or F</small>
      </div>

      <div class="form-group">
        <label>Email</label>
        <q-input
          outlined
          dense
          v-model="form.email"
          class="form-control"
          placeholder="Enter Email"
        />
        <small class="form-text text-muted">Type of emails</small>
      </div>

      <q-btn
        @click="btnSubmit"
        color="primary"
      >Submit</q-btn>
    </div>
    <q-markup-table>
      <thead>
        <tr>
          <th class="text-left">Name</th>
          <th class="text-right">Age</th>
          <th class="text-right">Gender</th>
          <th class="text-right">Email</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(customer,i) in customers"
          :key="i"
        >
          <td class="text-left">{{customer.name}}</td>
          <td class="text-right">{{customer.age}}</td>
          <td class="text-right">{{customer.gender}}</td>
          <td class="text-right">{{customer.email}}</td>
        </tr>
      </tbody>
    </q-markup-table>
  </div>
</template>
<script>
// eslint-disable-next-line semi
import axios from 'axios';
export default {
  data () {
    return {
      customers: [],
      form: {
        name: 'Jame',
        age: 20,
        gender: 'F',
        email: 'jmae@slfs.com'
      }
    }
  },
  mounted () {
    this.getData()
  },
  methods: {
    getData () {
      axios
        .get('http://192.168.0.105:3000/findCustomer')
        .then(response => {
          this.customers = response.data
        })
        .catch(e => {})
    },
    async btnSubmit () {
      axios
        .get('http://192.168.0.105:3000/insertCustomer', {
          params: this.form
        })
        .then(doc => {
          this.getData()
        })
        .catch(e => {})
    }
  }
}
</script>
