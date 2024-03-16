<script setup lang="Ts">
const props = defineProps(["account"]);
</script>

<template>
    <div class="wrapper">
        <h1>Ergebnisse</h1>
        <ol v-for="account in props.account" class="search-results">
            <li>
                <p>{{ account.uuid }}</p>
            </li>
        </ol>
    </div>
</template>

<style scoped>


</style>