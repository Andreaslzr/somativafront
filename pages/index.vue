<script setup>
    const {data:usuarios} = await useFetch('http://localhost:8000/usuarios')
</script>

<template>
    <div>
        <h1>Bem vindo</h1>
        <img src="https://img2.gratispng.com/20180409/dke/kisspng-login-facebook-computer-icons-button-clip-art-register-button-5acb4c08286176.2106116815232727121654.jpg" width="150" height="100">
        <h2>Login</h2>
        <select>
            <option v-for="usuario in usuarios.data" :key="usuario.id" :value="usuario.email">{{ usuario.email }}</option>
        </select> <br> <br>
        <NuxtLink to="/homepage">
            <button>Login</button>
        </NuxtLink> <br>
    </div>
</template>