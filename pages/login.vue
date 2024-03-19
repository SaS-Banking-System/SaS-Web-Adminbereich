<script setup lang="ts">
let adminUser = ref<string>("");
let adminPass = ref<string>("");
let loginRequest = ref<boolean>(false);

if (useCookie("bearerToken").value) await navigateTo("/");

async function login()
{
  if (String(adminUser.value) == null || String(adminUser.value) == '') {
    return;
  }
  if (String(adminPass.value) == null || String(adminPass.value) == '') {
    return;
  }

  loginRequest.value = true;

  const authRequest = await useFetch(
    "http://localhost:3001/auth/admin",
    {
      method: "post",
      body: {
        username: String(adminUser.value),
        password: String(adminPass.value),
      },
    },
  );

  if (!authRequest || authRequest.status.value === "error") {
    loginRequest.value = false;
    return;
  }

  const authData = JSON.stringify(authRequest.data.value);
  const authJsonObject = JSON.parse(authData);
  const bearerToken = authJsonObject.access_token;

  const bearerTokenCookie = useCookie("bearerToken");
  bearerTokenCookie.value = bearerToken;

  loginRequest.value = false;

  navigateTo("/");
}
</script>

<template>
  <div class="wrapper">
    <h1>Administratorbereich</h1>
    <form @submit.prevent="login">
      <input v-model="adminUser" placeholder="Benutzername" />
      <input v-model="adminPass" placeholder="Passwort" />
      <button :disabled="loginRequest" @click="login" class="login-button" type="submit">Einloggen</button>
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

form {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
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
  font-size: 1.5rem;
  outline: none;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

input:focus {
  outline: 2px solid rgba(125, 169, 252, 0.747);
}

.login-button {
  all: unset;
  font-size: 1.5rem;
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