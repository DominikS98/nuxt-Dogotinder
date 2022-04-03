<template>
  <div class="card" @click="moreInfo(dog)">
    <section class="card_image">
      <img :src="`${dog.image}`" />
      <div class="card_title title-white">
        <p>{{ dog.name }}</p>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  props: ["dog"],
  data() {
    return {};
  },
  methods: {
    moreInfo(data) {
      this.$emit("open-Info", data);
    },
  },
};
</script>
<style scoped>
.card {
  position: relative;
  min-width: 40vh;
  max-width: 20%;
  height: 300px;
  box-shadow: 5px 5px 30px 7px rgba(98, 47, 238, 0.3),
    -5px -5px 30px 7px rgba(98, 47, 238, 0.22);
  margin: 30px 10px;
  transition: 0.5s;
  border-radius: 10px;
  overflow: hidden;
}
.card:hover {
  transform: scale(0.9);
}
.card_image {
  position: relative;
  width: inherit;
  height: inherit;
}

.card_image img {
  width: inherit;
  height: inherit;
  object-fit: cover;
}
.card_title {
  position: relative;
  color: rgb(255, 251, 251);
  text-shadow: 0px 0px 5px rgb(5, 5, 5);
  top: -25%;
  text-align: center;
  font-size: 2rem;
}
</style>
