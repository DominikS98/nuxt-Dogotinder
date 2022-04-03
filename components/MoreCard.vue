<template>
  <div class="card">
    <span @click="$emit('close-Info')">X</span>
    <div class="card_img">
      <img :src="`${dog.image}`" />
    </div>
    <div class="card_data">
      <p><b>Nazwa: </b>{{ dog.name }}</p>
      <p><b>Wyskość: </b>{{ dog.height }} cm</p>
      <p><b>Długość: </b>{{ dog.weight }} cm</p>
      <p><b>Rasa do: </b>{{ dog.bred_for }}</p>
      <p><b>Grupa rasy: </b>{{ dog.breed_group }}</p>
      <p><b>Długość życia: </b>{{ dog.life_span }}</p>
      <p><b>Temperament: </b>{{ dog.temperament }}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: ["dog"],
};
</script>

<style scoped>
.card {
  position: fixed;
  display: flex;
  align-items: center;
  width: 60%;
  height: 50%;
  border-radius: 40px;
  top: 5%;
  background-color: rgba(0, 0, 0, 0.733);
  z-index: 10;
  box-shadow: 5px 5px 30px 7px rgba(98, 47, 238, 0.3),
    -5px -5px 30px 7px rgba(98, 47, 238, 0.22);
  transition: 0.5s;
  padding: 20px;
}
.card_img {
  margin: 0 10px;
  width: 35%;
  height: 300px;
}
.card_img img {
  object-fit: cover;
  max-width: 100%;
  height: 300px;
}
.card_title {
  width: 65%;
}
b {
  font-size: 3ch;
}
p {
  font-size: 2.7ch;
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
  color: rgb(255, 251, 251);
  text-shadow: 0px 0px 5px rgb(5, 5, 5);
}
span {
  position: absolute;
  right: 5%;
  top: 5%;
  color: aliceblue;
  font-size: 5ch;
  cursor: pointer;
  transition: 0.5s;
}
span:hover {
  transform: scale(0.9);
}
</style>
