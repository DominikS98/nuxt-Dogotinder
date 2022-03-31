<template>
  <div class="container">
    <section
      @click="pokaz"
      class="img"
      v-bind:style="{ backgroundImage: 'url(' + img + ')' }"
    ></section>
    <section class="name">
      <h3>{{ dog.name }}</h3>
    </section>

    <div class="more" :class="{ active: see }" v-if="see">
      <p if="dog.breed_group !== undefined ">
        <b>Dla kogo:</b>{{ dog.bred_for }}
      </p>
      <p if="dog.bred_for !== undefined"><b>Rasa:</b> {{ dog.name }}</p>
      <p if="dog.name !== undefined"><b>Okres życia:</b> {{ dog.life_span }}</p>
      <p if="dog.life_span !== undefined">
        <b>temperament:</b> {{ dog.temperament }}
      </p>
      <p>Wiecej o rasie tu:<a :href="link"> link</a></p>
    </div>

    <div @click="$emit('nope-event')" class="nope">&#9747;</div>
    <div @click="$emit('yes-event')" class="ok">&#10084;</div>
  </div>
</template>
<script>
export default {
  props: ["img", "dog"],
  data() {
    return {
      see: false,
      link: "https://www.google.com/search?q=" + this.dog.name,
    };
  },
  methods: {
    pokaz() {
      this.see = !this.see;
    },
  },
};
</script>

<style scoped>
.container {
  margin-top: 2rem;
  position: relative;
  min-width: 40%;
  height: 90vh;
  box-shadow: 1px 2px 30px rgba(0, 0, 0);
  border-radius: 40px;
  overflow: hidden;
}
.img {
  display: block;
  width: 100%;
  height: 80%;
  max-height: 80%;
  max-width: 100%;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
.name {
  position: relative;
  z-index: 2;
  bottom: 10%;
  left: 5%;
  color: rgb(255, 255, 255);
  text-shadow: 1px 1px 10px rgba(5, 5, 5, 0.897);
  text-transform: uppercase;
  font-size: 24px;
}
.ok,
.nope {
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
  cursor: pointer;
}
.more {
  position: absolute;
  background: rgba(245, 245, 245, 0.514);
  top: 10%;
  left: 10%;
  width: 80%;
  height: auto;
  padding: 5px;
  backdrop-filter: blur(10px);
}
.more p {
  font-size: 1.3rem;
}
a {
  color: black;
  text-decoration: none;
  font-weight: bold;
}
.nope {
  left: 10%;
}
.active {
  animation: see 1s both;
}
@media only screen and (max-width: 600px) {
  .container {
    width: 100%;
  }
  .img {
    width: 100%;
    height: 50%;
  }
  .more {
    top: 50%;
    left: 0;
    margin: auto 0;
    background: rgba(245, 245, 245, 0.514);
    width: 80%;
    padding: 5px;
    backdrop-filter: blur(10px);
  }
  .more p {
    margin: 0.5rem;
  }
  h3 {
    font-size: 1.3rem;
  }
}
@keyframes see {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
