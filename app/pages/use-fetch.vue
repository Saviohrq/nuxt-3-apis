<template>
    <h1>Use fetch</h1>

    <button @click="refresh">Recarregar Dados</button>

    <div v-if="pending">Carregando...</div>
    <div v-else-if="error">Erro: {{ error.message }}</div>

    <pre v-else>
        {{ charmander }}
    </pre>
</template>

<script setup>
const { 
    data: charmander, 
    pending, 
    error, 
    refresh,
 } = await useLazyFetch('https://pokeapi.co/api/v2/pokemon/charmander', {
    method: "GET",
    headers: {
        "Content-Type": "application/json"
    },
    transform: (data) => ({
        id: data.id,
        name: data.name,
        image: data.sprites.front_default
    }),
});
</script>