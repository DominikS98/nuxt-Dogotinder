<template>
  <div class="box">
    <minCard />
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
    //console.log(liczba);
    this.dogs = await fetch("https://api.thedogapi.com/v1/breeds", {
      headers: {
        "X-API-KEY": "b0a7328e-6b71-4693-a05d-b24a612d40e9",
      },
    }).then((res) => {
      // res.json();
      console.log(res.json());
    });
  },
  mounted() {
    this.$fetch();
  },
  methods: {},
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
</style>
