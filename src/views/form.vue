<template>
  <div>
    <br />
    <br />
    <br />
    <b-container>
      <b-row align-h="center">
        <b-col md="6">
          <form @submit="submitData">
            <b-form-group id="nombre" label="Nombre" label-for="nombre">
              <b-form-input
                id="input-1"
                v-model="name"
                type="text"
                required
                name="name"
                placeholder="Ingresa tu nombre"
              />
            </b-form-group>
            <b-form-group id="nombre" label="Imagen" label-for="nombre">
              <b-form-file
                v-model="file"
                :state="Boolean(file)"
                required
                placeholder="Escoge una imagen..."
                drop-placeholder="Deja caer la imagen aquí..."
              ></b-form-file>
            </b-form-group>
            <b-form-group id="nombre">
              <b-button type="submit" variant="success">Generar tarjeta</b-button>
            </b-form-group>
          </form>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      file: ""
    };
  },
  methods: {
    submitData(e) {
      e.preventDefault();
      this.$emit("formato", { name: this.name, file: this.file });
    }
  }
};
</script>

<style>
</style>