<template>
  <div class="box">
    <section class="Menu_box"><Menu /></section>
    <div class="tags_box">
      <input
        type="text"
        id="breeds"
        placeholder="Rasa"
        v-model="valueOfInput"
        @keyup="searchDogs"
      />

      <select
        v-model="valueOfdogFor"
        @change="searchdogFor"
        name="dogFor"
        id="dogFor"
      >
        <option value="" selected>Dla kogo</option>
        <option value="hunting">hunting</option>
        <option value="Sheep guarding">Sheep guarding</option>
        <option value="Guarding">Guarding</option>
        <option value="Sled pulling">Sled pulling</option>
      </select>

      <select
        v-model="valueOfTemperament"
        @change="searchTemperament"
        name="Temperament"
        id="Temperament"
      >
        <option value="" selected>Temperament</option>
        <option value="Wild">Wild</option>
        <option value="Hardworking">Hardworking</option>
        <option value="Dutiful">Dutiful</option>
        <option value="Friendly">Friendly</option>
      </select>
    </div>
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
      allDogs: [],
      foundDogs: [],
      valueOfInput: "",
      valueOfdogFor: "",
      valueOfTemperament: "",
    };
  },
  async asyncData() {
    const cos = await fetch("https://api.thedogapi.com/v1/breeds", {
      headers: {
        "X-API-KEY": "b0a7328e-6b71-4693-a05d-b24a612d40e9",
      },
    }).then((res) => {
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
      let bredsFor;
      let temperament;
      dogs.forEach((item) => {
        if (item.bred_for != undefined) {
          bredsFor = item.bred_for.split(",");
          temperament = item.temperament.split(",");
          for (let i = 0; i < bredsFor.length; i++) {
            bredsFor[i] = bredsFor[i].replace(" ", "");
          }
          for (let i = 0; i < temperament.length; i++) {
            temperament[i] = temperament[i].replace(" ", "");
          }
        }
        const dog = {
          id: item.id,
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
        this.allDogs.push(dog);
      });
      this.dogsTocomponent = this.allDogs;
    },
    info(data) {
      this.seeMoreAbaut = data;
    },
    close() {
      this.seeMoreAbaut = [];
    },
    searchDogs() {
      if (this.valueOfInput != "") {
        setTimeout(() => {
          this.foundDogs = [];
          this.dogsTocomponent.forEach((element) => {
            if (element.name.toLowerCase().includes(this.valueOfInput)) {
              this.foundDogs.push(element);
            }
          });
          this.dogsTocomponent = this.foundDogs;
        }, 1000);
      } else {
        this.dogsTocomponent = this.allDogs;
      }
    },
    searchdogFor() {
      if (this.valueOfdogFor != "") {
        if (this.valueOfTemperament != "") {
          let found = [];
          this.foundDogs.forEach((element) => {
            if (element.bred_for != undefined) {
              if (element.bred_for.includes(this.valueOfdogFor)) {
                if (this.foundDogs.find((item) => item.id != element.id)) {
                  found.push(element);
                }
              }
            }
          });
          this.dogsTocomponent = found;
        } else {
          this.foundDogs = [];
          this.allDogs.forEach((element) => {
            if (element.bred_for != undefined) {
              if (element.bred_for.includes(this.valueOfdogFor)) {
                this.foundDogs.push(element);
              }
            }
          });
          this.dogsTocomponent = this.foundDogs;
        }
      } else {
        this.dogsTocomponent = this.allDogs;
      }
    },

    searchTemperament() {
      if (this.valueOfTemperament != "") {
        if (this.valueOfdogFor != "") {
          let found = [];
          this.foundDogs.forEach((element) => {
            if (element.temperament != undefined) {
              if (element.temperament.includes(this.valueOfTemperament)) {
                if (this.foundDogs.find((item) => item.id != element.id)) {
                  found.push(element);
                }
              }
            }
          });
          this.dogsTocomponent = found;
        } else {
          this.foundDogs = [];
          this.allDogs.forEach((element) => {
            if (element.temperament != undefined) {
              if (element.temperament.includes(this.valueOfTemperament)) {
                this.foundDogs.push(element);
              }
            }
          });
          this.dogsTocomponent = this.foundDogs;
        }
      } else {
        this.dogsTocomponent = this.allDogs;
      }
    },
  },
};
//
</script>

<style scoped>
.box {
  display: flex;
  flex-flow: column;
  widows: 100%;
}
.card_box {
  padding: 0;
  margin: 3rem 0;
  display: flex;
  justify-content: center;
  align-content: center;
  align-items: center;
  flex-wrap: wrap;
  width: 100%;
  height: 100%;
}
.tags_box {
  margin: 5rem auto 0 auto;
  display: flex;
  justify-content: space-evenly;
  width: 70%;
}
.tags_box input {
  padding: 10px;
  font-size: 1.5rem;
  border: none;
  border-bottom: 1px solid rgba(0, 0, 0, 0.192);
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
  opacity: 0.5;
  transition: 0.5s;
}
select {
  padding: 0 20px;
  font-size: 1.5rem;
  border: none;
  border-bottom: 1px solid rgba(0, 0, 0, 0.192);
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
  opacity: 0.5;
  transition: 0.5s;
}
select:hover,
select:focus,
input:hover,
input:focus {
  opacity: 1;
  border-bottom: 1px solid black;
}
@media only screen and (max-width: 600px) {
  .tags_box {
    flex-flow: column;
  }
}
</style>
