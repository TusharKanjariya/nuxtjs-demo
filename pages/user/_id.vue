<template>
  <div>
    <b-card :title="userDetail.name" :sub-title="userDetail.email"></b-card>
    <nuxt-link to="/">Back to Home</nuxt-link>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'UserDetail',
  data() {
    return {
      userDetail: ''
    }
  },
  methods: {
    getDetails() {
      axios
        .get(
          `https://jsonplaceholder.typicode.com/users/${this.$route.params.id}`
        )
        .then(res => {
          this.userDetail = res.data
        })
    }
  },
  created() {
    this.getDetails()
  }
}
</script>