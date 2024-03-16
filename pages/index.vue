<script setup lang="ts">
const adminIDCookie = useCookie("adminid");

if (!adminIDCookie.value) await navigateTo("/login");
</script>

<template>   
    <Sidebar />
    <div class="page-content">
        <h1>Administratorbereich</h1>
        <p>Willkommen zum Administratorbereich. Hier können Sie auf das Banking-System zugreifen.
        <br>Auf der linken Seite finden Sie die Seitenleiste, mit dem man den Administratorbereich navigieren kann.
        </p>
    </div>
</template>

<style scoped>
.page-content {
    margin-left: 30px;
    padding: 1px 16px;
    height: 99vh;
    background-color: white;
    background-image: url("/gradientbackground.svg");
    background-repeat: no-repeat;
    background-size: cover;
}

h1 {
    font-size: 3rem;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

p {
    font-size: 1.3rem;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
</style>