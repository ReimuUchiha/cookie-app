<script setup lang="ts"></script>

<template>
  <div class="HeaderBackground">
    <img class="CatLogo" src="./icons/CookieLogo.png" />

    <div class="TitelContainer">
      <div class="TitelEins">Catfood-Tracker</div>
      <div class="TitelZwei"><img src="./icons/2000.gif" /></div>
    </div>
  </div>
</template>

<style>
.HeaderBackground {
  display: flex;
  top: 0px;
  left: 0px;
  width: 100vw;
  height: 10vh;
  background-color: #ffffff;
}

.CatLogo {
  width: auto;
  height: 10vh;
  float: left;
  border-radius: 50%;
}

.TitelContainer {
  top: 50px;
  width: 100%;
  display: flex;
  justify-content: center;

  gap: 20px;
}

.TitelEins {
  font-family: Sans-Serif;
  font-size: 60px;
  font-weight: bolder;

  padding-top: 25px;

  background: -webkit-linear-gradient(
    rgb(202, 10, 10),
    rgb(219, 178, 43),
    rgb(233, 111, 55)
  );
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.TitelZwei {
  font-size: 60px;
  font-weight: bolder;

  padding-top: 3px;

  background: -webkit-linear-gradient(
    rgb(202, 10, 10),
    rgb(219, 178, 43),
    rgb(233, 111, 55)
  );
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}
</style>
