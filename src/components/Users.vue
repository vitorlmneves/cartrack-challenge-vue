<template>
    <transition-group name="bounce" tag="div" id="js-content" class="users">
      <div v-for="(user, index) in usersList"
          :key="index"
          class="users__content"
          >
        <div class="users__item users__item--user">{{user.name}}</div>
        <div class="users__item">{{user.company.name}}</div>
        <div class="users__item"><a v-bind:href="'mailto:' + user.email" class="users__link">{{user.email}}</a></div>
        <div class="users__item"><a v-bind:href="user.phone" class="users__link">{{user.phone}}</a></div>
        <div class="users__item">{{user.website}}</div>
        <div class="users__item users__item--address">{{user.address.city}}</div>
        <a v-bind:href="user.phone" class="users__button">
          <i class="icon-phone"></i>
          Contact
        </a>
      </div>
      <div v-if="usersList.length === 0" id="js-no-results" class="no-results">
        <p class="no-results__msg">No results found</p>
      </div>
  </transition-group>
</template>

<script>

export default {
  name: 'users',
  components: {
    // NoResults
  },
  props:{
    usersList: Array,
  },
  data() {
    return {};
  }
}
</script>
