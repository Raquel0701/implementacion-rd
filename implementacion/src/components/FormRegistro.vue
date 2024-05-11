<template>
    <div class="form-container" style="margin: 2em;">
        <BreadcrumbRd :items="breadcrumbItems" />

        <HeadingRd class="heading-rd h1" level="1">Formulario de Solicitud</HeadingRd>

        <form @submit.prevent="handleSubmit" style=" text-align: left;">
            <InputRd id="name" label="Nombre Completo" v-model="formData.name"
                placeholder="Ingresa tu nombre completo" />
            <br>
            <InputRd id="email" label="Correo Electrónico" v-model="formData.email" type="email"
                placeholder="Ingresa tu correo electrónico" />

            <br>
            <TextareaRd id="description" label="Descripción" v-model="formData.description"  size="2" 
                placeholder="Describe brevemente tu solicitud" />

            <br>
            <ButtonRd :severity="primary" @accion="handleSubmit">Enviar</ButtonRd>
            <ButtonRd severity="danger" @accion="handleReset()" type="button">Limpiar</ButtonRd>


            <ModalRd :show="showModal" @close="toggleModal">
                <p>{{ modalMessage }}</p>
            </ModalRd>
        </form>
    </div>
</template>

<script>
import { BreadcrumbRd, ButtonRd, HeadingRd, InputRd, TextareaRd, ModalRd } from 'components-rd';

export default {
    name: 'FormPage',
    components: {
        BreadcrumbRd,
        ButtonRd,
        HeadingRd,
        InputRd,
        TextareaRd,
        ModalRd
    },
    data() {
        return {
            formData: {
                name: '',
                email: '',
                description: ''
            },
            showModal: false,
            modalMessage: 'Gracias por tu registro!',
            breadcrumbItems: [
                { label: 'Inicio', url: '/' },
                { label: 'Registro', url: '/register' }
            ]
        };
    },
    methods: {
        handleSubmit() {
            this.modalMessage = 'Formulario enviado con éxito!';
            this.showModal = true;
        },
        handleReset() {
            console.log("elimiandoo")
            this.formData.name = '';
            this.formData.email = '';
            this.formData.description = '';
        },

        toggleModal() {
            this.showModal = !this.showModal;
        }
    }
}
</script>

<style scoped>
.form-container {
    max-width: 600px;
    margin: auto;
}
</style>