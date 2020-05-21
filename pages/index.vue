<template>
  <div>
    <h1 class="display-4">List of Users</h1>
    <b-list-group>
      <b-list-group-item v-for="u in user" :key="u.id" :to="'user/' + u.id">{{u.name}}</b-list-group-item>
    </b-list-group>
  </div>
</template>

<script>
import axios from 'axios'
import { BIconTrash2 } from 'bootstrap-vue'
export default {
  name: 'user',
  components: {
    BIconTrash2
  },
  data() {
    return {
      user: []
    }
  },
  methods: {
    getData() {
      axios.get('https://jsonplaceholder.typicode.com/users').then(res => {
        this.user = res.data
      })
    },
    deleteUser(id) {
      $event.stopPropagation()
      this.user.splice(id, 1)
    }
  },
  created() {
    this.getData()
  }
}
</script>

<style scoped>
</style>x