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
                id="nombre"
                v-model="name"
                type="text"
                required
                name="name"
                placeholder="Ingresa tu nombre"
              />
            </b-form-group>
            <b-form-group id="nombre" label="Celular" label-for="phone">
              <b-form-input
                id="phone"
                v-model="phone"
                type="tel"
                required
                name="phone"
                placeholder="Ingresa tu celular"
              />
            </b-form-group>
            <b-form-group id="nombre" label="Imagen">
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
      file: "",
      phone: ""
    };
  },
  methods: {
    submitData(e) {
      e.preventDefault();
      this.$emit("formato", {
        name: this.name,
        file: this.file,
        phone: this.phone
      });
    }
  }
};
</script>

<style>
</style>