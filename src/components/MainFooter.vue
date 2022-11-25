<script setup lang="ts">
</script>

<template>
    <div class="FooterBackground">
        <div class="Socials">
            <button onclick="window.location.href='https://www.facebook.com/midlight.gmbh/';" class="Facebook">Facebook</button>
            <button onclick="window.location.href='https://www.instagram.com/chax.at/';" class="Instagram">Instagram</button>
            <button onclick="window.location.href='https://www.linkedin.com/uas/login?session_redirect=https%3A%2F%2Fwww.linkedin.com%2Fcompany%2Fchax-at-midlight-gmbh%2Fposts%2F%3FfeedView%3Dall/';" class="LinkedIn">LinkedIn</button>
            <button onclick="window.location.href='https://chax.at/';" class="Chax">Chax</button>     
        </div>
    </div>
</template>

<style>
body {
  font-family: Sans-Serif;
  min-height: 100vh;
  margin: 0;
}

.FooterBackground {
  position: absolute;
  height: 10vh;
  width: 100vw;
  bottom: 0;
  background-color: #ffffff93;
}

.Socials {
  width: 150px;
  display: flex;
  margin-top: 20px;
  margin-left: 90vw;
  gap: 5px;
  flex-direction: column;
}

</style>
