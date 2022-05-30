<template>
  <div>
    <Menu class="menu" />
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
        <p>
          Lorem Ipsum is simply dummy text of the printing and typesetting
          industry. Lorem Ipsum has been the industry's standard dummy text ever
          since the 1500s, when an unknown printer took a galley of type and
        </p>
        <NuxtLink to="/dodaj">więcej</NuxtLink>
      </div>
      <div class="podStrony_box rasy">
        <h4>wszystie rasy</h4>
        <p>
          Lorem Ipsum is simply dummy text of the printing and typesetting
          industry. Lorem Ipsum has been the industry's standard dummy text ever
          since the 1500s, when an unknown printer took a galley of type and
        </p>
        <NuxtLink to="/przeglondaj">więcej</NuxtLink>
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
    </section>
    <div class="boxColor">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320">
        <path
          fill="#00cba9"
          fill-opacity="1"
          d="M0,64L48,80C96,96,192,128,288,138.7C384,149,480,139,576,128C672,117,768,107,864,90.7C960,75,1056,53,1152,80C1248,107,1344,181,1392,218.7L1440,256L1440,320L1392,320C1344,320,1248,320,1152,320C1056,320,960,320,864,320C768,320,672,320,576,320C480,320,384,320,288,320C192,320,96,320,48,320L0,320Z"
        ></path>
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
};
</script>

<style scoped>
div {
  overflow-x: hidden;
  margin: 0;
}
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
  font-size: 8vw;
  background: linear-gradient(
    53deg,
    rgb(19, 255, 98) 0%,
    rgba(83, 83, 83, 1) 46%,
    #0c7fcb 100%
  );
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
}
.title h2 {
  font-size: 3vh;
}
.greenCircle {
  position: absolute;
  background-color: #00cba9;
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
  font-size: 2vw;
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
  color: #0099ff;
  bottom: 5%;
  right: 5%;
  transform: rotate(-25deg);
  font-size: 2vw;
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
  min-height: 50vh;
}
.podStrony_box {
  width: 20%;
  height: 200px;
  box-shadow: 2px 2px 30px 10px rgba(0, 0, 0, 0.5);
  background-color: whitesmoke;
  z-index: 1;
  display: flex;
  flex-flow: column;
  justify-content: center;
  padding: 20px;
  overflow: hidden;
  transition: 0.7s;
}
.podStrony_box:after {
  content: " ";
  transition: 0.7s;
  width: 100%;
  height: 80%;
  position: absolute;
  left: 0;
  bottom: 0;
  background: linear-gradient(
    0deg,
    rgba(255, 255, 255, 1) 0%,
    rgba(255, 255, 255, 0.795) 30%,
    rgba(255, 255, 255, 0) 100%
  );
}
.podStrony_box:hover:after {
  opacity: 0;
}
.podStrony_box:hover {
  height: 300px;
}
.podStrony_box h4 {
  margin-top: 4rem;
  font-size: 2.2vw;
  text-align: center;
}
.podStrony_box a {
  text-align: left;
  color: black;
  z-index: 1;
}
.blueCircle {
  position: absolute;
  background-color: #0099ff;
  padding: 300px;
  z-index: -2;
  border-radius: 50%;
  left: -10%;
  top: -10%;
}
.quiz {
  position: relative;
  display: flex;
  flex-flow: column;
  width: 70%;
  justify-content: center;
  align-content: center;
  margin: 0 auto;
  text-align: center;
}
.quiz h2 {
  font-size: 4vw;
}
.quiz p {
  font-size: 1.5vw;
}
.boxColor {
  position: relative;
  left: -2%;
  bottom: -2%;
  width: 120%;
  height: 50%;
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
@media only screen and (max-width: 600px) {
  .witold {
    flex-flow: column;
    justify-content: center;
    align-items: center;
  }
  .obrazek {
    width: 70%;
  }
  .text_Witoldzie {
    font-size: 5vw;
    width: 90%;
  }
  .podStrony {
    flex-flow: column;
    align-items: center;
  }
  .podStrony_box {
    width: 70%;
  }
  .podStrony_box h4 {
    font-size: 5vw;
  }
  .quiz {
    width: 90%;
  }
  .quiz h2 {
    font-size: 9vw;
  }
  .quiz p {
    font-size: 5vw;
    text-align: left;
  }
}
</style>
