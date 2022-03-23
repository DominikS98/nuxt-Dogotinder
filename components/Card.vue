<template>
  <div>
    <section
      class="img"
      v-bind:style="{ backgroundImage: 'url(' + img + ')' }"
    ></section>
    <section class="name">
      <h3>{{ nameDog }}</h3>
    </section>

    <div @click="$emit('nope-event')" class="nope">&#9747;</div>
    <div @click="$emit('yes-event')" class="ok">&#10084;</div>
  </div>
</template>
<script>
export default {
  props: ["img", "nameDog"],
};
</script>

<style scoped>
div {
  margin-top: 2rem;
  position: relative;
  width: 30%;
  height: 90vh;
  box-shadow: 1px 2px 30px rgba(0, 0, 0);
  border-radius: 40px;
  overflow: hidden;
}
.img {
  display: block;
  width: 100%;
  height: 100%;
  max-height: 100%;
  max-width: 100%;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
.name {
  position: relative;
  z-index: 2;
  bottom: 25%;
  left: 10%;
  color: rgb(255, 255, 255);
  text-shadow: 1px 1px 10px rgba(5, 5, 5, 0.897);
  text-transform: uppercase;
  font-size: 24px;
}
.ok {
  z-index: 10;
  position: absolute;
  padding: 40px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.205);
  bottom: 5%;
  right: 10%;
  margin-top: 0;
  width: 0%;
  height: 0%;
  box-shadow: 1px 2px 10px rgba(0, 0, 0);
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 3em;
  font-weight: bolder;
}
.nope {
  z-index: 10;
  position: absolute;
  padding: 40px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.205);
  bottom: 5%;
  left: 10%;
  margin-top: 0;
  width: 0%;
  height: 0%;
  box-shadow: 1px 2px 10px rgba(0, 0, 0);
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 3em;
  font-weight: bolder;
}
@media only screen and (max-width: 600px) {
  div {
    width: 100%;
  }
}
</style>
