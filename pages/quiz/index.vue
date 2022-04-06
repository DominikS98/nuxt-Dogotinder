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
              ><input name="answer" type="radio" value="A: " />A:
              {{ questions[currentQuestion].odpA }}</label
            >
            <label>
              <input name="answer" type="radio" value="B: " />B:
              {{ questions[currentQuestion].odpB }}
            </label>
            <label>
              <input name="answer" type="radio" value="C: " />C:
              {{ questions[currentQuestion].odpC }}
            </label>
            <label v-if="questions[currentQuestion].odpD != ''">
              <input name="answer" type="radio" value="D: " />D:{{
                questions[currentQuestion].odpD
              }}
            </label>
          </span>
        </section>
        <section class="box__quiz--footer">
          <button v-if="currentQuestion < 3" @click="nextQuetion">
            następne
          </button>
          <button v-else>podsumowanie</button>
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
      questions: [
        {
          pytanie: "wielkość psa",
          odpA: "Duży",
          odpB: "średni",
          odpC: "mały",
          odpD: "",
        },
        {
          pytanie: "Pies stworzony do",
          odpA: "Obrony",
          odpB: "Tropienia",
          odpC: "Rodziny",
          odpD: "Zawodów",
        },
        {
          pytanie: "Usposobienie psa",
          odpA: "Szcześliwy",
          odpB: "Inteligentny",
          odpC: "Lojalny",
          odpD: "Aktywny",
        },
        {
          pytanie: "długość życias",
          odpA: "mniej niż 10lat",
          odpB: "10-12",
          odpC: "12-14",
          odpD: "wiecej niż 14",
        },
      ],
    };
  },
  methods: {
    nextQuetion() {
      this.currentQuestion = this.currentQuestion + 1;
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
  justify-content: end;
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
