<script setup>
    const {data:tarefas} = await useFetch('http://localhost:8000/tarefas?all')
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
        <h1>Tarefas:</h1>
        <div v-for="tarefa in tarefas.data" :key="tarefa.id">
            <span> <strong>Nome: </strong>{{ tarefa.nome }} | </span>
            <span> <strong>Status: </strong>{{ tarefa.idStatusFK.nome }} | </span>
            <span> <strong>Ambiente: </strong>{{ tarefa.idAmbienteFK.nome }} | </span>
            <span> <strong>Prazo: </strong>{{ tarefa.prazo }} </span> <br>
            <NuxtLink :to="`/tarefas/${tarefa.id}`">
                <button>Abrir tarefa</button>
            </NuxtLink> <br>
            <br>
        </div>
    </div>
</template>