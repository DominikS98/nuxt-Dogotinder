<template>
  <div class="box">
    <section class="Menu_box"><Menu /></section>
    <section class="card_box">
      <MinCard
        v-for="dog in this.dogsTocomponent"
        :key="dog.name"
        :dog="dog"
        @open-Info="info"
      />
      <MoreCard
        v-if="seeMoreAbaut != ''"
        :dog="seeMoreAbaut"
        @close-Info="close"
      />
    </section>
  </div>
</template>
<script>
export default {
  data() {
    return {
      seeMoreAbaut: "",
      dogsTocomponent: [],
    };
  },
  async asyncData() {
    const cos = await fetch("https://api.thedogapi.com/v1/breeds", {
      headers: {
        "X-API-KEY": "b0a7328e-6b71-4693-a05d-b24a612d40e9",
      },
    }).then((res) => {
      //console.log(res.json());
      return res.json();
    });
    return { cos };
  },

  mounted() {
    this.useData();
  },
  methods: {
    useData() {
      const dogs = this.cos;
      dogs.forEach((item) => {
        const dog = {
          breed_group: item.breed_group,
          height: item.height.metric,
          weight: item.weight.metric,
          bred_for: item.bred_for,
          name: item.name,
          life_span: item.life_span,
          temperament: item.temperament,
          image: item.image.url,
          name: item.name,
        };
        this.dogsTocomponent.push(dog);
      });
    },
    info(data) {
      this.seeMoreAbaut = data;
    },
    close() {
      this.seeMoreAbaut = [];
    },
  },
};
//
</script>

<style scoped>
.card_box {
  padding: 0;
  margin: 0;
  display: flex;
  justify-content: center;
  align-content: center;
  align-items: center;
  flex-wrap: wrap;
  width: 100%;
  height: 100%;
}
</style>
