<template>
  <div>
    <Menu></Menu>
    <section class="box">
      <div class="box__quiz">
        <section class="box__quiz--header">
          <h1>Pytanie nr {{ currentQuestion + 1 }}:</h1>
          <span class="questions">
            <div
              v-bind:class="this.currentQuestion >= 1 ? 'blue' : 'black'"
            ></div>
            <div
              v-bind:class="this.currentQuestion >= 2 ? 'blue' : 'black'"
            ></div>
            <div
              v-bind:class="this.currentQuestion >= 3 ? 'blue' : 'black'"
            ></div>
            <div
              v-bind:class="this.currentQuestion >= 4 ? 'blue' : 'black'"
            ></div>
          </span>
        </section>
        <section class="box__quiz--body">
          <h2>tresć pytania:</h2>
          <p>{{ questions[currentQuestion].pytanie }}</p>
          <span class="answer">
            <label
              ><input
                name="answer"
                v-model="an"
                type="radio"
                :value="questions[currentQuestion].odpA.val"
              />A: {{ questions[currentQuestion].odpA.answer }}</label
            >
            <label>
              <input
                name="answer"
                v-model="an"
                type="radio"
                :value="questions[currentQuestion].odpB.val"
              />B:
              {{ questions[currentQuestion].odpB.answer }}
            </label>
            <label>
              <input
                name="answer"
                v-model="an"
                type="radio"
                :value="questions[currentQuestion].odpC.val"
              />C:
              {{ questions[currentQuestion].odpC.answer }}
            </label>
            <label v-if="questions[currentQuestion].odpD.answer != ''">
              <input
                name="answer"
                v-model="an"
                type="radio"
                :value="questions[currentQuestion].odpD.val"
              />D:{{ questions[currentQuestion].odpD.answer }}
            </label>
          </span>
        </section>
        <section class="box__quiz--footer">
          <button v-if="currentQuestion < 3" @click="nextQuetion">
            następne
          </button>
          <button v-else @click="findDong">podsumowanie</button>
        </section>
      </div>
    </section>
  </div>
</template>
<script>
export default {
  data() {
    return {
      currentQuestion: 0,
      an: "",
      tableAns: [],
      dogsTab: [],
      questions: [
        {
          pytanie: "wielkość psa",
          odpA: {
            answer: "Duży",
            val: "40",
          },
          odpB: {
            answer: "Średni",
            val: "20-30",
          },
          odpC: {
            answer: "Mały",
            val: "20",
          },
          odpD: {
            answer: "",
            val: "50",
          },
        },
        {
          pytanie: "Pies stworzony do",
          odpA: {
            answer: "Obrony",
            val: "guardian",
          },
          odpB: {
            answer: "Tropienia",
            val: "hunting",
          },
          odpC: {
            answer: "Rodziny",
            val: "Companionship",
          },
          odpD: {
            answer: "Ratowniczy",
            val: "Trailing",
          },
        },
        {
          pytanie: "Usposobienie psa",
          odpA: {
            answer: "Szcześliwy",
            val: "Happy",
          },
          odpB: {
            answer: "Inteligentny",
            val: "Intelligent",
          },
          odpC: {
            answer: "Lojalny",
            val: "Loyal",
          },
          odpD: {
            answer: "Aktywny",
            val: "Active",
          },
        },
        {
          pytanie: "długość życias",
          odpA: {
            answer: "mniej niż 10lat",
            val: "10",
          },
          odpB: {
            answer: "10-12",
            val: "10-12",
          },
          odpC: {
            answer: "12-14",
            val: "12-14",
          },
          odpD: {
            answer: "wiecej niż 14",
            val: "14",
          },
        },
      ],
    };
  },
  async asyncData() {
    const dogsAsync = await fetch("https://api.thedogapi.com/v1/breeds", {
      headers: {
        "X-API-KEY": "b0a7328e-6b71-4693-a05d-b24a612d40e9",
      },
    }).then((res) => {
      return res.json();
    });
    return { dogsAsync };
  },
  methods: {
    nextQuetion() {
      if (this.currentQuestion < 3)
        this.currentQuestion = this.currentQuestion + 1;
      this.tableAns.push(this.an);
    },
    findDong() {
      this.tableAns.push(this.an);
      const dogs = this.dogsAsync;
      dogs.forEach((item) => {
        if (
          (item.height.metric.includes(this.tableAns[0]) &&
            item.height.metric != undefined) ||
          (item.bred_for.includes(this.tableAns[1]) &&
            item.bred_for != undefined) ||
          (item.temperament.includes(this.tableAns[2]) &&
            item.temperament != undefined) ||
          (item.life_span.includes(this.tableAns[3]) &&
            item.life_span != undefined)
        ) {
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
          this.dogsTab.push(dog);
        }

        console.log(this.dogsTab);
      });
      // if(element > )

      //      Guarding    Happy         <10
      // smal  <30      hunting   Intelligent   10- 12
      // medium  <40     Family   Loyal         12 -14
      // big  >40       search    Active        >14
    },
  },
};
</script>
<style scoped>
.box {
  margin-top: 2rem;
  min-height: 90vh;
  display: flex;
  justify-content: center;
  align-content: center;
  align-items: center;
}
.box__quiz {
  border: 1px solid black;
  padding: 10px 50px;
  display: flex;
  flex-flow: column;
  box-shadow: 10px 10px 30px 10px rgba(0, 0, 0, 0.4);
}

.questions {
  display: flex;
  justify-content: space-evenly;
  width: 100%;
}
h1 {
  font-size: 3em;
  margin-top: 0;
  margin-bottom: 1rem;
  position: relative;
  left: -10%;
}
.questions div {
  position: relative;
  left: -10%;
  height: 0px;
  max-width: 20%;
  width: 100%;
  margin: 4px;
  border: 1px solid rgb(68, 68, 68);
  border-radius: 50%;
  transition: 1s;
}

.answer {
  display: flex;
  flex-flow: column;
  margin: 1rem 0;
}
.answer label {
  margin: 0.5rem 0;
}
input {
  opacity: 0.5;
  transition: 0.5s;
}
input:hover {
  opacity: 1;
}
.box__quiz--footer {
  display: flex;
  justify-content: flex-end;
}
.blue {
  border-color: rgb(28, 3, 255) !important;
}
.black {
  border: 1px solid rgb(0, 0, 0);
}
button {
  position: relative;
  right: -10%;
  background-color: inherit;
  border: none;
  font-size: 1em;
  font-weight: bold;
  opacity: 0.5;
  transition: 0.5s;
  margin: 5px;
  padding: 5px;
}
button:hover {
  opacity: 1;
  color: rgb(28, 3, 255);
}
</style>
