<template>
  <div id="app">
    <Search @filterUser="filterUser"></Search>
    <Spinner />
    <Users :usersList="usersListAux"></Users>
  </div>
</template>

<script>
import Spinner from './components/Spinner.vue'
import Users from './components/Users.vue'
import Search from './components/Search.vue'

export default {
  name: 'app',

  components: {
    Spinner,
    Users,
    Search
  },

  data () {
    return {
      usersList: [],
      usersListAux: []
    }
  },

  methods: {
    /**
     *
     * @param {String} search
     */
    filterUser(search) {
      this.usersListAux = []

      for (let user of this.usersList) {
        if (user.name.toLowerCase().includes(search.toLowerCase())) {
          this.usersListAux.push(user)
        }
      }
    },

    async getUsers () {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users')
        const data = await response.json()

        document.getElementById('js-spinner').style.opacity = '0'
        document.getElementById('js-content').style.opacity = '1'

        this.usersList = data
        this.usersListAux = data
      } catch (error) {
          throw new Error(error)
      }
    }
  },

  mounted () {
    this.getUsers()
  }
}
</script>
