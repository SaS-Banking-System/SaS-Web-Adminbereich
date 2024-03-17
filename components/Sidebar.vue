<script setup lang="ts">

function signOut()
{
    const bearerTokenCookie = useCookie("bearerToken");
    bearerTokenCookie.value = null;

    location.reload();
}
</script>

<template>
    <div class="sidebar">
        <NuxtLink to="/" class="side-bar-item home-link">Hauptseite</NuxtLink>
        <NuxtLink to="/search" class="sidebar-item">Konten</NuxtLink>
        <button class="sign-out-button" @click="signOut">Ausloggen</button>
    </div>
</template>

<style scoped>
:global(body) {
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.sidebar {
    margin: 0;
    padding: 0;
    position: fixed;
    width: 250px;
    height: 100%;
    overflow: auto;
    box-shadow: 0px;
    background-color: rgb(97, 100, 104);
    left: -220px;
    transition: 0.3s;
}

.sidebar:hover {
    left: 0px;
    box-shadow: 6px 2px 15px 0px rgba(58, 58, 58, 0.3);
}

button {
    all: unset;
    display: block;
    color: white;
    padding: 10px;
    font-size: 1.4rem;
}

button:hover {
    cursor: pointer;
    background-color: rgb(0, 0, 0, 0.3);
}

.open-button {
    color: black;
}

.sign-out-button {
    margin-top: 83vh;
}

a {
    all: unset;
    display: block;
    color: white;
    padding: 10px;
    font-size: 1.4rem;
}

a:hover {
    background-color: rgb(0, 0, 0, 0.3);
    cursor: pointer;
}

.home-link {
    font-weight: bold;
}
</style>