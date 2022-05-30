<template>
  <div class="card">
    <div class="blue"></div>
    <div class="green"></div>
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
  overflow: hidden;
  width: 60%;
  border-radius: 40px;
  top: 10%;
  background-color: rgba(255, 255, 255, 0.808);
  z-index: 10;
  box-shadow: 5px 5px 30px 7px rgba(98, 47, 238, 0.3),
    -5px -5px 30px 7px rgba(98, 47, 238, 0.22);
  transition: 0.5s;
  padding: 20px;
}
.card_img {
  margin: 0 10px;
  min-width: 30%;
  max-width: 30%;
  transform: skew(10deg, -10deg);
  overflow: hidden;
  margin: 3rem;
}
.card_img img {
  object-fit: cover;
  max-width: 100%;
}
.card_title {
  width: 65%;
}
b {
  font-size: 3ch;
}
p {
  font-size: 3ch;
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
  color: rgba(7, 0, 0, 0.788);
  text-shadow: 0px 0px 5px rgb(77, 76, 76);
}
p::after {
  position: absolute;
  display: block;
  content: "";
  border: 1px solid rgb(71, 231, 119);
  width: 10%;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
span {
  position: absolute;
  right: 5%;
  top: 5%;
  color: rgb(0, 0, 0);
  font-size: 5ch;
  cursor: pointer;
  transition: 0.5s;
}
span:hover {
  transform: scale(0.9);
}
.blue,
.green {
  padding: 250px;
  position: absolute;
  z-index: -1;
  border-radius: 50% 30%;
}
.green {
  left: -10%;
  top: -20%;
  background-color: rgba(49, 238, 49, 0.781);
}
.blue {
  right: -10%;
  bottom: -20%;
  background-color: rgba(69, 122, 236, 0.781);
}
@media only screen and (max-width: 600px) {
  .card {
    top: 5%;
    width: 90%;
    height: 70vh;
    flex-flow: column;
  }
  .card_img {
    display: none;
  }
}
</style>
