<template>
  <div>
    <transition-group name="users__content" tag="div" class="users">
      <div v-for="user in usersList"
          :key="user.id"
          class="users__content"
          >
      <div class="users__item users__item--user">{{user.name}}</div>
      <div class="users__item">{{user.company.name}}</div>
      <div class="users__item">
        <a v-bind:href="'mailto:' + user.email" class="users__link">{{user.email}}</a>
      </div>
      <div class="users__item">
        <a v-bind:href="user.phone" class="users__link">{{user.phone}}</a>
      </div>
      <div class="users__item">{{user.website}}</div>
      <div class="users__item users__item--address">{{user.address.city}}</div>
      <a v-bind:href="user.phone" class="users__button">
        <i class="icon-phone"></i>
        Contact
      </a>
    </div>
  </transition-group>
  <div v-if="usersList.length === 0" class="no-results">
    <p class="no-results__msg">No results found</p>
  </div>
</div>
</template>

<script>
export default {
  name: 'users',

  props: {
    usersList: {
      type: Array,
      required: true
    }
  }
}
</script>
