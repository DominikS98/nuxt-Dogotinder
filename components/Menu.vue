<template>
  <nav>
    <ul class="menu" v-bind:class="{ OpenMenu: menuOn }">
      <li>
        <NuxtLink to="/psiTinder">Psitinder </NuxtLink>
      </li>
      <li>
        <NuxtLink to="/przeglondaj">Zobacz rasy </NuxtLink>
      </li>
      <li>
        <NuxtLink to="/">Strona główna</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/quiz">Quiz</NuxtLink>
      </li>
    </ul>
    <span @click="openMenu" class="hamburger">
      <div></div>
      <div></div>
      <div></div>
    </span>
  </nav>
</template>
<script>
export default {
  data() {
    return {
      menuOn: false,
    };
  },
  methods: {
    openMenu() {
      this.menuOn = !this.menuOn;
    },
  },
};
</script>
<style scoped>
a.nuxt-link-active {
  font-weight: bold;
}
/* exact link will show the primary color for only the exact matching link */
a.nuxt-link-exact-active {
  color: #00c58e;
}

ul {
  display: flex;
  list-style: none;
  justify-content: space-evenly;
  align-items: center;
  background-color: rgba(69, 122, 236, 0.856);
  padding: 20px;
  position: fixed;
  width: 100%;
  top: -2%;
  left: 0;
  z-index: 10;
}
a {
  color: white;
  text-decoration: none;
  font-size: 1.5rem;
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
}
.hamburger {
  display: none;
}
@media only screen and (max-width: 600px) {
  ul {
    transition: 0.5s;
    flex-flow: column;
    transform: translateY(-200px);
  }
  .hamburger {
    display: block;
    position: absolute;
    top: 10px;
    right: 10px;
    cursor: pointer;
    z-index: 10;
  }
  .hamburger div {
    border: 1px solid black;
    padding: 0px 10px;
    margin: 4px;
  }
  .OpenMenu {
    transform: translateY(0px);
  }
}
</style>
