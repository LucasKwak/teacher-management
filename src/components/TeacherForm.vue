<template>
    <section class="teacher-section">
        <h2>AÑADIR UN PROFESOR</h2>
        <form class="teacher-form">
            <fieldset class="teacher-form__wrapper-set">
                <legend>Información del profesor</legend>
                <div class="teacher-form__wrapper-input">
                    <label class="teacher-form__label" for="nombre">Nombre</label>
                    <input class="teacher-form__input" type="text" id="nombre">
                </div>
                <div class="teacher-form__wrapper-input">
                    <label class="teacher-form__label" for="apellidos">Apellidos</label>
                    <input class="teacher-form__input" type="text" id="apellidos">
                </div>
                <div class="teacher-form__wrapper-input">
                    <label class="teacher-form__label" for="dni">DNI</label>
                    <input class="teacher-form__input" type="text" id="dni">
                </div>
                <div class="teacher-form__wrapper-input teacher-form__materias">
                    <label class="teacher-form__label" for="materias">Materias</label>
                    <input class="teacher-form__input" type="text" id="materias">
                    <button class="materias__button">Añadir</button>
                </div>
            </fieldset>
        </form>
    </section>
</template>

<script lang="ts" setup>

</script>

<style scoped>
    .teacher-section {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .teacher-form {
        width: 500px;
    }

    .teacher-form__wrapper-set {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 10px;
    }

    .teacher-form__wrapper-input {
        display: flex;
        flex-direction: row;
        width: 400px;
        gap: 40px;
    }

    .teacher-form__label {
        width: 100px;
    }

    .materias__button {
        font-family: Avenir;
        background-color: blueviolet;
        color: white;
        border: 1px solid blueviolet;
        outline: 0;
    }

    .materias__button:hover{
        background-color: white;
        color: blueviolet;
        border: 1px solid blueviolet;
        box-sizing: content-box;
    }

</style>
