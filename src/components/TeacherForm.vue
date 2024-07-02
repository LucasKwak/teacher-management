<template>
    <section class="teacher-section">
        <h2>AÑADIR UN PROFESOR</h2>
        <form class="teacher-form">
            <fieldset class="teacher-form__wrapper-set">
                <legend>Información del profesor</legend>
                <div class="teacher-form__wrapper-input">
                    <label class="teacher-form__label" for="nombre">Nombre</label>
                    <input class="teacher-form__input" type="text" id="nombre" v-model="teacher.name">
                </div>
                <div class="teacher-form__wrapper-input">
                    <label class="teacher-form__label" for="apellidos">Apellidos</label>
                    <input class="teacher-form__input" type="text" id="apellidos" v-model="teacher.surname">
                </div>
                <div class="teacher-form__wrapper-input">
                    <label class="teacher-form__label" for="dni">DNI</label>
                    <input class="teacher-form__input" type="text" id="dni" v-model="teacher.dni">
                </div>
                <div class="teacher-form__wrapper-input teacher-form__materias">
                    <label class="teacher-form__label" for="materias">Materias</label>
                    <input class="teacher-form__input" type="text" id="materias" v-model="subject">
                    <button class="form__button" title="Añadir materia" type="button" @click="addSubject">Añadir</button>
                </div>
                <div class="teacher-form__wrapper-input teacher-form__materias-añadidas">
                    <p>Materias añadidas</p>
                    <ul>
                        <li v-for="(subj, index) in teacher.subjects" :key="index">{{ subj }}</li>
                    </ul>
                </div>
                <div class="teacher-form__wrapper-input teacher-form__materias">
                    <label class="teacher-form__label" for="documentacion">Documentación entregada</label>
                    <input class="teacher-form__input" type="checkbox" id="documentacion"  v-model="teacher.documentation">
                </div>
            </fieldset>
            <button class="form__button" type="button" @click="addTeacher">Añadir profesor</button>
        </form>
    </section>

    <section>
        <h2>LISTADO DE PROFESORES DADOS DE ALTA</h2>
    </section>
</template>

<script lang="ts" setup>
    import { Ref, ref } from 'vue';

    interface ITeacher {
        name: string,
        surname: string,
        dni: string,
        subjects: Array<string>,
        documentation: boolean
    }

    // ARRAY DE PROFESORES GLOBAL
    let teachers: Ref<Array<ITeacher>> = ref([]);
    
    // PROFESOR POR CADA USO DEL FORMULARIO
    let teacher:Ref<ITeacher> = ref({
        name: '',
        surname: '',
        dni: '',
        subjects: [],
        documentation: false
    });
    
    // MATERIA POR CADA USO DEL INPUT DE MATERIAS (se añade a las materias de profesor correspondiente)
    let subject: Ref<string> = ref('');

    // FUNCION PARA AÑADIR UNA MATERIA A UN PROFESOR
    function addSubject() {
        if(subject.value == ''){
            alert("Escriba una materia primero");
        }else{
            teacher.value.subjects.push(subject.value);
            subject.value = '';
        }
    }

    // FUNCION PARA AÑADIR UN PROFESOR
    function addTeacher() {
        teachers.value.push(
            {
                name: teacher.value.name,
                surname: teacher.value.surname,
                dni: teacher.value.dni,
                subjects: teacher.value.subjects,
                documentation: teacher.value.documentation,
            }
        );
        teacher.value.name = '';
        teacher.value.surname = '';
        teacher.value.dni = '';
        teacher.value.subjects = [];
        teacher.value.documentation = false;
    }

</script>

<style scoped>
    .teacher-section {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .teacher-form {
        width: 500px;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 15px;
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

    .teacher-form__materias-añadidas {
        max-height: 200px;
    }

    .teacher-form__materias-añadidas p {
        font-style: italic;
    }

    .teacher-form__materias-añadidas ul {
        width: 150px;
        overflow-y: scroll;
    }

    .teacher-form__label {
        width: 100px;
    }

    .form__button {
        font-family: Avenir;
        background-color: blueviolet;
        color: white;
        border: 1px solid blueviolet;
        outline: 0;
    }

    .form__button:hover{
        background-color: white;
        color: blueviolet;
        border: 1px solid blueviolet;
        box-sizing: content-box;
    }

</style>
