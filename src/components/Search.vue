<template>
    <section class="search">
      <h1 class="search__title">{{title}}</h1>
      <input type="search"
        id="js-search-input"
        name="search"
        class="search__input"
        placeholder="Search"
        v-model="search"
        @keyup="searchUsers(search)"
        @search="searchUsers(search)"
      />
      <i class="icon-search"></i>
    </section>
</template>

<script>
export default {
  data () {
    return {
      title: 'Search Your Team',
      search: ''
    }
  },

  methods: {
    searchUsers (search) {
      this.$emit('filterUser', search)
    }
  }
}
</script>

<style scoped lang="scss">
.search {
  margin: 30px auto 60px;
  padding: 0;
  position: relative;
  width: 300px;
}

.search__title {
  font-weight: $font-weight-thin;
  text-align: center;
}

.search__input {
  border: 2px solid $silver;
  border-radius: 3px;
  color: $silver;
  font-size: .9rem;
  padding: 5px 40px 5px 10px;
  width: 100%;
}

.search .icon-search {
  bottom: 6px;
  position: absolute;
  right: 6px;
}
</style>
