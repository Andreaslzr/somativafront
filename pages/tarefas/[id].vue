<script setup>
    const route = useRoute();
    const {data:tarefas} = await useFetch(`http://localhost:8000/tarefas/${route.params.id}`)

    const {data:responsaveis} = await useFetch(`http://localhost:8000/tarefasUsuarios?tarefa=${route.params.id}`)

    const {data:status} = await useFetch(`http://localhost:8000/tarefasStatus?tarefa=${route.params.id}`)
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
        <h1>Tarefa: {{ tarefas.data.id }}</h1>
        <h4> <strong>Nome: </strong> {{ tarefas.data.nome }} | </h4>
        <h4> <strong>Status: </strong>{{ tarefas.data.idStatusFK.nome }} | </h4>
        <h4> <strong>Ambiente: </strong>{{ tarefas.data.idAmbienteFK.nome }} | </h4>
        <h4> <strong>Prazo: </strong>{{ tarefas.data.prazo }} </h4>
        <h4> <strong>Data de inicio: </strong>{{ tarefas.data.dataInicio }} </h4>
        <h4> <strong>Data de término: </strong>{{ tarefas.data.dataFim }} </h4>
        <h4> <strong>Descrição: </strong>{{ tarefas.data.descricao }} </h4> 
        <h4> <strong>Solicitante: </strong> </h4>
        <h4>{{ tarefas.data.idSolicitanteFK.nome }}</h4>
        <img :src="tarefas.data.idSolicitanteFK.image" width="150" height="100"> <br> <br>
        <h4>Responsaveis:</h4>
        <div v-for="responsavel in responsaveis.data" :key="responsavel.id">
            <span>{{ responsavel.idUsuarioFK.nome }}</span> <br> 
            <img :src="responsavel.idUsuarioFK.image" width="150" height="100"> <br> <br>
        </div> <br>
        <h4>Status:</h4>
        <div v-for="stat in status.data" :key="stat.id">
            <span>{{ stat.idStatusFK.nome}}</span>  <br>
            <span>Data: {{ stat.data}}</span> <br> <br>
        </div> <br>
    



        

    
    </div>
</template>