<script setup lang="Ts">
</script>

<template>
    <div class="wrapper">
        <h1>Suchergebnisse:</h1>
        <ol class="search-results">
            <li>
                <SearchResult />
            </li>
        </ol>
    </div>
</template>

<style scoped>
.wrapper {
    display: flex;
    flex-direction: column;
}

.search-results {
    padding: 0;
    width: 50%;
    list-style-type: none;
}

h1 {
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    font-size: 1.5rem;
}
</style>