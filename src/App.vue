<template>
    <header>
        <h1>SISTEMA DE GESTIÓN DEL PROFESORADO</h1>
    </header>
    <main>
        <TeacherForm></TeacherForm>
    </main>
</template>

<script lang="ts" setup>
    import TeacherForm from './components/TeacherForm.vue';
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: #2c3e50;
        margin-top: 20px;
    }

    h1 {
        margin: 0;
        text-align: center;
    }
</style>
