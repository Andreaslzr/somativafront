<script setup>
    const {data:cargos} = await useFetch('http://localhost:8000/cargos')
</script>

<template>
    <div>
        <h3>Menu</h3>
        <div>
            <NuxtLink to="/homepage">Home</NuxtLink> <br>
            <NuxtLink to="/ambientes">Ambientes</NuxtLink> <br>
            <NuxtLink to="/cargos">Cargos</NuxtLink> <br>
            <NuxtLink to="/tarefas">Tarefas</NuxtLink> <br>
        </div>
        <h1>Cargos:</h1>
        <div v-for="cargo in cargos.data" :key="cargo.id">
            <span> <strong>Nome: </strong>{{ cargo.nome }} |  </span>
            <span> <strong>Nivel de acesso: </strong>{{ cargo.nivelAcesso }} </span>
        </div>
    </div>
</template>