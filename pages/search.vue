<script setup lang="ts">
const adminIDCookie = useCookie("adminid");

if (!adminIDCookie.value) await navigateTo("/login");

const showModal = ref(false);
const scannedUUID = ref("");

function handleUUID(uuid: string) {
    scannedUUID.value = uuid;
}

function searchUUID() {
    
}
</script>

<template>   
    <Sidebar />
    <div class="page-content">
        <h1>Kontenbereich</h1>
        <form @submit.prevent="searchUUID">
            <input :value="scannedUUID" class="search-bar" placeholder="Gebe eine UUID ein oder scanne eine Kontenkarte..."/>
            <button class="qr-scan-button" @click="showModal = true" type="button">
                <img width="27" height="27" src="/camera.svg"/>
            </button>
            <div class="modalWrapper">
                <QRscanModal
                :show="showModal"
                @close="showModal = false"
                @sendUUID="handleUUID"
                ></QRscanModal>
             </div>
        </form>
        <SearchResults />
    </div>
</template>

<style scoped>
.page-content {
    margin-left: 30px;
    padding: 1px 16px;
    height: 99vh;
    background-color: white;
    background-image: url("/dashboardbg2.svg");
    background-repeat: no-repeat;
    background-size: cover;
}

h1 {
    font-size: 3rem;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

form {
    width: 50%;
    padding: 1px;

    display: flex;
    flex-direction: row;
    border: 1px solid gray;
    border-radius: 5px;
}

form:focus-within {
    outline: 1px solid rgb(0, 140, 255);
}

.search-bar {
    font-size: 1.3rem;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    flex-grow: 2;
    border: none;
}

.search-bar:focus {
    outline: none;
}

.qr-scan-button {
    all: unset;
    width: 27px;
}

img {
    opacity: 0.5;
    margin-top: 3px;
}

img:hover {
    opacity: 1;
    cursor: pointer;
}
</style>