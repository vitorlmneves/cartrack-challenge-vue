<template>
  <div class="users" id="js-content">
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
  <div v-if="usersList.length === 0" id="js-no-results" class="no-results">
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

<style lang="scss" scoped>
.users {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 0 auto;
  max-width: 1200px;
}

.users__content {
border: 2px solid $silver;
border-radius: 3px;
padding: 10px 10px 40px;
position: relative;
margin: 0 30px 50px;
width: 300px;

.users-move {
  transition: all 600ms ease-in-out 50ms
}

.users-enter-active {
  transition: all 300ms ease-out
}

.users-leave-active {
  transition: all 200ms ease-in;
  position: absolute;
  z-index: 0;
}

.users-enter,
.users-leave-to {
  opacity: 0
}

.users-enter {
  transform: scale(0.9)
}

.users__item {
  align-items: center;
  display: flex;
  font-size: .9rem;
  margin-bottom: 10px;
  text-indent: 10px;
  transform-origin: 10% 50%;
  z-index: 1;

  &:before {
    content: "";
    font-size: 1.2rem;
    margin-right: 10px;
    width: 30px;
  }
}

.users__item--user {
  font-size: 1.1rem;
  font-weight: $font-weight-bold;
  margin-bottom: 5px;

    &:before {
      content: "\e900";
      font-family: $font-icons;
      font-weight: $font-weight-regular;
    }
}

.users__item--address {

    &:before {
      content: "\e902";
      font-family: $font-icons;
    }
  }
}

.users__link {
  color: $default-font-color;
  text-decoration: none;

  &:hover {
    text-decoration: underline;
  }
}

.users__button {
  align-items: center;
  background: transparent;
  border: 2px solid $silver;
  bottom: 10px;
  color: $default-font-color;
  cursor: pointer;
  display: flex;
  font-size: .8rem;
  padding: 5px 10px;
  position: absolute;
  right: 10px;
  text-decoration: none;

  & .icon-phone {
    padding-right: 10px;
  }

  &:hover {
    background: $silver;
    color: $white;
  }
}

.no-results {
  margin: 0 auto;
  text-align: center;
  width: 100%;
}

.no-results__msg {
  font-size: 2rem;
  font-weight: $font-weight-thin;
}
</style>
