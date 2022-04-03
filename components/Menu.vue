<template>
  <ul>
    <li>
      <NuxtLink to="/dodaj">Psitinder </NuxtLink>
    </li>
    <li>
      <NuxtLink to="/przeglondaj">Zobacz rasy </NuxtLink>
    </li>
    <li>
      <NuxtLink to="/">Strona główna</NuxtLink>
    </li>
  </ul>
</template>

<style space>
ul {
  display: flex;
  list-style: none;
  justify-content: space-evenly;
  align-items: center;
  background-color: rgba(98, 47, 238, 0.575);
  padding: 20px;
  position: fixed;
  width: 100%;
  top: -2%;
  left: 0;
  z-index: 10;
}
li {
}
a {
  color: white;
  text-decoration: none;
  font-size: 1.5rem;
}
</style>
