<template>
  <div class="card">
    <section class="card_image">
      <img src="https://cdn2.thedogapi.com/images/BJa4kxc4X.jpg" />
      <div class="card_title title-white">
        <p>Card Title</p>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      img: "https://cdn2.thedogapi.com/images/BJa4kxc4X.jpg",
    };
  },
};
</script>
<style scoped>
.card {
  position: relative;
  min-width: 20%;
  max-width: 20%;
  height: 300px;
  box-shadow: 5px 5px 30px 7px rgba(0, 0, 0, 0.25),
    -5px -5px 30px 7px rgba(0, 0, 0, 0.22);
  margin: 30px 0;
  transition: 0.5s;
  border-radius: 40px;
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
  top: -20%;
  text-align: center;
}
</style>
