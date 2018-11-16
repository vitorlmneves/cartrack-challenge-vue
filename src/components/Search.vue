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
      />
      <button type="button" id="js-search" class="search__button" disabled>
        <i class="icon-search"></i>
      </button>
    </section>
</template>

<script>
export default {
  data() {
    return {
      title: "Search Your Team",
      search: ''
    }
  },
  methods: {
    searchUsers: function(search) {
      this.$emit('filterUser', search);
    }
  }
}
</script>
