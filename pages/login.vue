<script setup lang="ts">
let adminID = ref<string>("");

if (useCookie("adminid").value) await navigateTo("/");

async function login()
{
  if (!String(adminID.value).match(/^[0-9]{2,4}$/g)) {
    return;
  }

  //check for valid id

  const adminIDCookie = useCookie("adminid");
  adminIDCookie.value = adminID.value;

  navigateTo("/");
}
</script>

<template>
  <div class="wrapper">
    <h1>Administratorbereich</h1>
    <form @submit.prevent="login">
      <input v-model="adminID" type="number" placeholder="Admin-ID" />
      <button class="login-button" type="submit">Einloggen</button>
    </form>
  </div>
</template>

<style scoped>
.wrapper {
  position: absolute;
  background-color: white;
  filter: drop-shadow(0px 0px 7px rgb(201, 201, 201));
  padding: 50px;
  padding-top: 20px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
h1 {
  font-size: 2.6rem;
  margin-bottom: 3rem;
  text-align: center;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

input {
  all: unset;
  border: 1px solid rgb(180, 180, 180);
  border-radius: 5px;
  padding: 10px;
  font-size: 1.3rem;
  outline: none;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

input:focus {
  outline: 2px solid rgba(125, 169, 252, 0.747);
}

.login-button {
  all: unset;
  font-size: 1.3rem;
  margin-left: 1.1rem;
  cursor: pointer;
  background-color: rgb(38, 189, 126);
  color: white;
  padding: 0.7rem;
  border-radius: 5px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.login-button:hover {
  background-color: rgb(52, 156, 95);
}
</style>