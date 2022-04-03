<template>
  <div class="box">
    <section class="Menu_box"><Menu /></section>
    <Card
      class="card"
      :img="this.parts"
      :dog="this.breeds"
      @yes-event="szukaj"
    />
  </div>
</template>
<script>
export default {
  data() {
    return {
      dogs: [],
      parts: "",
      breeds: {
        breed_group: "brak danych",
        bred_for: "brak danych",
        name: "brak danych",
        life_span: "brak danych",
        temperament: "brak danych",
      },
    };
  },
  async fetch() {
    const liczba = Math.floor(Math.random() * (197 - 1));
    //console.log(liczba);
    this.dogs = await fetch(
      "https://api.TheDogAPI.com/v1/images/search?breed_ids=" + liczba,
      {
        headers: {
          "X-API-KEY": "b0a7328e-6b71-4693-a05d-b24a612d40e9",
        },
      }
    ).then((res) => res.json());
    this.szukaj();
  },
  mounted() {
    this.$fetch();
  },
  methods: {
    szukaj() {
      if (Array.isArray(this.dogs) && this.dogs.length) {
        this.parts = this.dogs[0].url;
        if (Array.isArray(this.dogs[0].breeds) && this.dogs[0].breeds.length) {
          if (this.dogs[0].breeds[0] !== undefined) {
            this.breeds.breed_group = this.dogs[0].breeds[0].breed_group;
          }
          if (this.dogs[0] !== undefined) {
            console.log(this.dogs.bred_for);
            this.breeds.bred_for = this.dogs[0].breeds[0].bred_for;
          }
          if (this.dogs[0].breeds[0] !== undefined) {
            console.log(this.dogs[0].breeds[0].name);
            this.breeds.name = this.dogs[0].breeds[0].name;
          }
          if (this.dogs[0].breeds[0] !== undefined) {
            console.log(this.dogs[0].breeds[0].life_span);
            this.breeds.life_span = this.dogs[0].breeds[0].life_span;
          }
          if (this.dogs[0].breeds[0] !== undefined) {
            console.log(this.dogs[0].breeds[0].temperament);
            this.breeds.temperament = this.dogs[0].breeds[0].temperament;
          }
          this.$fetch();
        } else {
          this.$fetch();
        }
      } else {
        this.$fetch();
      }
    },
  },
};
//
</script>

<style scoped>
.box {
  padding: 0;
  margin: 0;
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
.card {
  margin-top: 4rem;
}
</style>
