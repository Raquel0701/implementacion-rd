<template>
  <div style="margin: 2em;">
    <h1>Heading</h1>
    <hr>
    <HeadingRd class="heading-rd h1" level="1">Encabezado de Nivel 1</HeadingRd><br>
    <HeadingRd class="heading-rd h2" level="2">Encabezado de Nivel 2</HeadingRd><br>
    <HeadingRd class="heading-rd h3" level="3">Encabezado de Nivel 3</HeadingRd><br>
    <hr>
    <h1>Button</h1>
    <div style=" display: grid;  grid-auto-flow: column;">

      <div v-for="(button, index) in buttons" :key="index">
        <ButtonRd :severity="button.severity" @accion="handleAccionClick">
          {{ button.label }}
        </ButtonRd>
      </div>
    </div>
    <hr>
    <div>


      <button class="button-rd button-primary">Botón Predeterminado</button>
      <button class="button-rd button-primary button-sm">Botón Pequeño</button>
      <button class="button-rd button-primary button-lg">Botón Grande</button>
      <button class="button-rd button-primary button-xl">Botón Extra Grande</button>
      <button class="button-rd button-primary button-xxl">Botón Extra Extra Grande</button>
    </div>
    <hr>
    <h1>BreadcrumbItems</h1>
    <BreadcrumbRd :items="breadcrumbItems" />
    <hr>
    <h1>Input</h1>

    <InputRd id="Input" label="Ejemplo de Input" type="text" placeholder="Ingresa" />
    Solo Style
    <input class="input-rd input-md">
    <hr>
    <h1>Textarea</h1>
    <TextareaRd id="myTextarea" label="Descripción" placeholder="Ingresa tu descripción aquí" size="1" />
    <TextareaRd id="myTextarea" label="Descripción" placeholder="Ingresa tu descripción aquí" size="2" />
    <TextareaRd id="myTextarea" label="Descripción" placeholder="Ingresa tu descripción aquí" size="3" />
    <TextareaRd id="myTextarea" label="Descripción" placeholder="Ingresa tu descripción aquí" size="4" />

    <!-- Modal normal -->

    <ButtonRd severity="primary" @accion="showModal = true"> Abrir Modal </ButtonRd>
    <ModalRd :show="showModal" @close="showModal = false">
      <h2>¡Este es un modal!</h2>
      <p>Aquí puedes agregar cualquier contenido que desees mostrar dentro del modal.</p>
    </ModalRd>

    <!-- Modal pequeño -->

    <ButtonRd severity="primary" @accion="showSmallModal = true"> Mostrar Modal Pequeño </ButtonRd>
    <ModalRd :show="showSmallModal" :size="sizeSm" @close="showSmallModal = false">
      <h2>¡Este es un modal!</h2>
      Contenido del Modal Pequeño
    </ModalRd>

    <!-- Modal grande -->

    <ButtonRd severity="primary" @accion="showLargeModal = true"> Mostrar Modal Grande </ButtonRd>
    <ModalRd :show="showLargeModal" :size="sizeLg" @close="showLargeModal = false">
      <h2>¡Este es un modal!</h2>
      Contenido del Modal Grande
    </ModalRd>

    <!-- Modal extra grande -->
    <ButtonRd severity="primary" @accion="showExtraLargeModal = true"> Mostrar Modal Extra Grande </ButtonRd>
    <ModalRd :show="showExtraLargeModal" :size="sizeXl" @close="showExtraLargeModal = false">
      <h2>¡Este es un modal!</h2>
      Contenido del Modal Extra Grande
    </ModalRd>
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
      ],
      buttons: [
        { label: 'Botón Primario', severity: 'primary' },
        { label: 'Botón Secundario', severity: 'secondary' },
        { label: 'Botón de Éxito', severity: 'success' },
        { label: 'Botón de Información', severity: 'info' },
        { label: 'Botón de Advertencia', severity: 'warning' },
        { label: 'Botón de Ayuda', severity: 'help' },
        { label: 'Botón de Peligro', severity: 'danger' },
        { label: 'Botón de Contraste', severity: 'contrast' },

      ],

      textareaValue: '',
      showSmallModal: false,
      showLargeModal: false,
      showExtraLargeModal: false,
      sizeSm: "sm",
      sizeLg: "lg",
      sizeXl: "xl",
    };
  },
  methods: {
    handleSubmit() {
      this.modalMessage = 'Formulario enviado con éxito!';
      this.showModal = true;
    },
    handleReset() {
      this.formData = { name: '', email: '', description: '' };
    },
    toggleModal() {
      this.showModal = !this.showModal;
    }
  }
}
</script>

<style scoped>
/* .form-container {
  max-width: 600px;
  margin: auto;
}

.button-group {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
} */
</style>
