<script setup>
    const {data:ambientes} = await useFetch('http://localhost:8000/ambientes')

    let show = false;
    const setShow = () => {
        show = true;
        refreshNuxtData()
    }    

    let nomeAmb;

    const send = async () => {
        await useFetch('http://localhost:8000/ambientes/',{
            method: 'POST',
            body: [ {
                nome: nomeAmb,
            } ],
            key: 'ambiente'
        })
    }
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
        <h1>Ambientes:</h1>
        <div v-for="ambiente in ambientes.data" :key="ambiente.id">
            <span> <strong>Nome: </strong>{{ ambiente.nome }}   </span>
        </div> <br>


        <button @click="setShow">Cadastrar novo ambiente</button>         
        <section v-if="show === true">
            <div>
                <label for="">Nome do ambiente:</label> <input type="text" v-model="nomeAmb"> <br>
            </div>
            <button @click="send">Cadastrar</button>
        </section>

    </div>
</template>