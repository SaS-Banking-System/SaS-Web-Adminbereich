<script setup lang="Ts">

</script>

<template>
    <button class="wrapper">
        <div class="info-header">
            <p>Vorname: Berkay</p>
            <p>Nachname: Kaya</p>
        </div>
        <div class="info-footer">
            <p class="user-balance">
                Guthaben: 20
                <img src="/dollar.svg" />
            </p>
            <p>Gesperrt: </p>
        </div>
    </button>
</template>

<style scoped>

:global(body)
{
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.wrapper {
    all: unset;
    border-bottom: 1px solid rgb(95, 95, 95);
    width: 50%;
    padding-left: 0.2rem;
    padding-top: 0.5rem;
    padding-bottom: 0.5rem;
}

.wrapper:hover {
    cursor: pointer;
    background-color: rgb(214, 214, 214);
}

.info-header {
    display: flex;
    gap: 1rem;
}

.info-footer {
    display: flex;
    gap: 1.5rem;
}

p {
    font-size: 1.2;
    font-weight: 500;
}

.user-balance {
    display: flex;
}

img {
    margin-top: 0.15rem;
    margin-left: 0.1rem;
    width: 1rem;
    color: black;
}
</style>