<template>
  <div>
    <Menu />
    <section class="title">
      <div class="greenCircle"></div>
      <h1>Witaj na PsiStronie</h1>
      <h2>Witold jest wesoły ze jesteś tu</h2>
    </section>
    <section class="witold">
      <div class="obrazek">
        <img src="https://cdn2.thedogapi.com/images/A09F4c1qP.jpg" />
        <h3>to jest Witold</h3>
      </div>
      <div class="text_Witoldzie">
        <h2>Co tu znajdziesz</h2>
        <p>
          Lorem Ipsum is simply dummy text of the printing and typesetting
          industry. Lorem Ipsum has been the industry's standard dummy text ever
          since the 1500s, when an unknown printer took a galley of type and
          scrambled it to make a type specimen book. It has survived not only
        </p>
      </div>
    </section>
    <section class="podStrony">
      <div class="podStrony_box">
        <h4>psitinder</h4>
        <p>jakis opis</p>
      </div>
      <div class="podStrony_box rasy">
        <h4>wszystie rasy</h4>
        <p>jakis opis</p>
      </div>
      <div class="blueCircle"></div>
    </section>
    <section class="quiz">
      <div>
        <h2>quiz</h2>
        <p>
          Lorem Ipsum is simply dummy text of the printing and typesetting
          industry. Lorem Ipsum has been the industry's standard dummy text ever
          since the 1500s, when an unknown printer took a galley of type and
          scrambled it to make a type specimen book. It has survived not only
          five centuries, but also the leap into electronic typesetting,
          remaining essentially unchanged. It was popularised in the 1960s with
          the release of Letraset sheets containing Lorem Ipsum passages, and
          more recently with desktop publishing software like Aldus PageMaker
          including versions of Lorem Ipsum.
        </p>
      </div>
      <div class="boxColor"></div>
    </section>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
};
</script>

<style scoped>
div {
  padding: 0;
  margin: 0;
  display: flex;
  flex-flow: column;
  position: relative;
  font-family: Cambria, Cochin, Georgia, Times, "Times New Roman", serif;
}
.title {
  margin-top: 5rem;
  text-align: center;
  border-bottom: 1px solid rgba(204, 204, 204, 0.582);
  margin-bottom: 1rem;
}
.title h1 {
  font-size: 8em;
}
.title h2 {
  font-size: 3em;
}
.greenCircle {
  position: absolute;
  background-color: rgb(80, 238, 80);
  padding: 300px;
  z-index: -1;
  border-radius: 50%;
  right: -10%;
  top: -10%;
}
.witold {
  position: relative;
  display: flex;
  justify-content: space-evenly;
}
.text_Witoldzie {
  width: 40%;
  font-size: 3ch;
  line-height: 150%;
}
.obrazek {
  width: 30%;
  box-shadow: 4px 5px 20px 9px rgba(0, 0, 0, 0.5);
}
.obrazek img {
  height: 100%;
  width: 100%;
  object-fit: cover;
  animation: outlineOut 1s forwards;
}
.obrazek h3 {
  position: absolute;
  color: rgb(68, 71, 238);
  bottom: 5%;
  right: 5%;
  transform: rotate(-25deg);
  font-size: 2rem;
  text-shadow: 1px 1px 4px rgb(253, 253, 253);
  z-index: 2;
}
img:hover {
  animation: outlineIn 1s forwards;
}
.podStrony {
  position: relative;
  display: flex;
  justify-content: space-evenly;
  margin-top: 5rem;
}
.podStrony_box {
  width: 30%;
  box-shadow: 2px 2px 30px 10px rgba(0, 0, 0, 0.5);
  background-color: whitesmoke;
  z-index: 1;
}
.blueCircle {
  position: absolute;
  background-color: rgb(70, 29, 219);
  padding: 300px;
  z-index: -2;
  border-radius: 50%;
  left: -10%;
  top: -10%;
}

@keyframes outlineIn {
  0% {
    outline: solid 0px rgb(255, 255, 255);
    outline-offset: 0px;
  }
  100% {
    outline: solid 1px rgb(255, 255, 255);
    outline-offset: -40px;
  }
}
@keyframes outlineOut {
  0% {
    outline: solid 1px rgb(255, 255, 255);
    outline-offset: -40px;
  }
  100% {
    outline: solid 0px rgb(255, 255, 255);
    outline-offset: 0px;
  }
}
</style>
