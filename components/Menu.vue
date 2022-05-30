<template>
  <ul>
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
</template>

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
@media only screen and (max-width: 600px) {
}
</style>
