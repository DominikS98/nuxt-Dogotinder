<template>
  <div class="box">
    <Card
      :img="this.dogs.message"
      :nameDog="this.parts"
      @yes-event="yes"
      @nope-event="$fetch"
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      dogs: [],
      parts: "",
      like: [],
    };
  },
  async fetch() {
    this.dogs = await fetch("https://dog.ceo/api/breeds/image/random").then(
      (res) => res.json()
    );
    this.rasa();
  },
  methods: {
    rasa() {
      const par = this.dogs.message;
      let parts = par.split("breeds/", 2);
      parts = parts[1].split("/", 2);
      this.parts = parts[0];
    },
    yes() {
      this.like.push(this.parts);
      console.log(this.like);
      this.$fetch();
    },
  },
};
//
</script>

<style scoped>
.box {
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
</style>
