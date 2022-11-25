<script setup lang="ts">
</script>

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

@keyframes rotation{
  from{
  transform: rotate(0deg);
  }

  to{
  transform: rotate(359deg);
  }

}

.HeaderBackground{
  display: flex;
  top: 0px;
  left: 0px;
  width: 100vw;
  height: 10vh;
  background-color: #ffffff93;
}


.CatLogo{
  animation: rotation 3s infinite;
  transform: rotate(360deg);
  width: auto;
  height: 10vh;
  float: left;
  border-radius: 50%;
}

.TitelContainer{
  top: 50px;
  width: 100%;
  display: flex;
  justify-content: center;
  gap: 20px;
}

.TitelEins{
  font-family: Sans-Serif;
  font-size: 60px;
  font-weight: bolder;
  padding-top: 25px;
  background: -webkit-linear-gradient(
    rgb(21, 81, 192),
    rgb(61, 250, 250),
    rgb(55, 228, 213)
  );
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.TitelZwei{
  padding-top: 3px;  
}

</style>
