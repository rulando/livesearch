<template>
  <b-container fluid>
    <b-row>
      <b-col md="6">
        <h2 v-if="!selected">Please Select User</h2>
        <b-card bg-variant="light" v-if="selected">
          <b-form-group breakpoint="lg"
                        label="Detail User"
                        label-size="lg"
                        label-class="font-weight-bold pt-0"
                        class="mb-0">
            <b-form-group horizontal
                          label="Name:"
                          label-class="text-sm-right"
                          label-for="nestedStreet">
              <b-form-input id="nestedStreet" v-model="user.name" disabled></b-form-input>
            </b-form-group>
            <b-form-group horizontal
                          label="Username:"
                          label-class="text-sm-right"
                          label-for="nestedCity">
              <b-form-input id="nestedCity" v-model="user.username" disabled></b-form-input>
            </b-form-group>
            <b-form-group horizontal
                          label="Email:"
                          label-class="text-sm-right"
                          label-for="nestedState">
              <b-form-input id="nestedState" v-model="user.email" disabled></b-form-input>
            </b-form-group>
            <b-form-group horizontal
                          label="City:"
                          label-class="text-sm-right"
                          label-for="nestedCountry">
              <b-form-input id="nestedCountry" v-model="user.address.city" disabled></b-form-input>
            </b-form-group>
            <b-form-group horizontal
                          label="Zipcode:"
                          label-class="text-sm-right"
                          label-for="nestedCountry">
              <b-form-input id="nestedCountry" v-model="user.address.zipcode" disabled></b-form-input>
            </b-form-group>
            <b-form-group horizontal
                          label="Phone:"
                          label-class="text-sm-right"
                          label-for="nestedCountry">
              <b-form-input id="nestedCountry" v-model="user.phone" disabled></b-form-input>
            </b-form-group>
            <b-form-group horizontal
                          label="Website:"
                          label-class="text-sm-right"
                          label-for="nestedCountry">
              <b-form-input id="nestedCountry" v-model="user.website" disabled></b-form-input>
            </b-form-group>
          </b-form-group>
        </b-card>
      </b-col>
      <b-col md="6">
        <b-form-input v-model="filter" type="search" placeholder="Type here.." size="lg">
        </b-form-input>
        <div class="list-user">
          <b-row>
            <b-col md="6" v-for="user in filteredUser" :key="user.id" class="user">
              <b-card :title="user.name">
                <p>@{{ user.username }}</p>
                <b-button variant="primary" @click="selectUser(user.id)">Detail</b-button>
              </b-card>
            </b-col>
          </b-row>
        </div>
      </b-col>
    </b-row>
  </b-container>
</template>
<script>
export default {
  props: ['users'],
  data () {
    return {
      selected: false,
      filter: '',
      user: {}
    }
  },
  methods: {
    selectUser (id) {
      this.user = this.users.filter(function (item) { return item.id === id }).pop()
      this.selected = true
    }
  },
  computed: {
    filteredUser () {
      return this.users.filter(user => {
        return user.name.toLowerCase().includes(this.filter.toLowerCase())
      })
    }
  }
}
</script>
<style>

.user{
  padding: 10px;
}
</style>
