<script setup lang="ts">
import router from '@/router';


var username = ""
var password = ""

function handleLoginClick() {
  if(username.length > 1 && password.length > 7) {
    updateErrorMsg("");
    router.push("/home")
  } else {
    updateErrorMsg("Invalid creds");
  }
}

function updateErrorMsg(errMsg: string) {
  var errorLabel = document.querySelector("label[id=loginstatusLabel]")
  if(errorLabel != null) errorLabel.textContent = errMsg;
}

</script>

<template>
  <div id="loginContainer">
    <div id="loginTitle">
      <label>Please login!</label>
    </div>
    <div id="username">
      <label id="usernameLabel">Username:</label>
      <textarea v-model="username"></textarea>
    </div>
    <div id="password">
      <label id="passwordLabel">Password: </label>
      <textarea v-model="password"></textarea>
      <button id="signinbutton" v-on:click="handleLoginClick">Sign in</button>
      <label id="loginstatusLabel"></label>
    </div>
  </div>
</template>

<style scoped>
  #loginContainer {
    display: grid;
    justify-content: center;
    margin: 40px;
  }

  #loginTitle {
      font-size: x-large;
      font-weight: bold;
      margin-bottom: 20px;
  }
  
  #username,
  #password {
    display: flex;
    flex-direction: row;
    align-items: center;
    column-gap: 20px;
  }
  
  #usernameLabel,
  #passwordLabel {
    width: 100px;
  }

</style>
