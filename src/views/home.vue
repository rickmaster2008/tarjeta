<template>
  <div id="container">
    <div id="background" ref="card">
      <div
        v-if="imageData.length > 0"
        id="picture"
        :style="{background: `url(${imageData})`, 'background-size': 'cover', 'background-position': 'center'}"
      ></div>
      <h1 id="name">{{name.toUpperCase()}}</h1>
      <h1 id="phone">{{phone}}</h1>
    </div>
    <div id="download-button" @click="downloadCard">
      <font-awesome-icon icon="download" size="2x" />
    </div>
  </div>
</template>

<script>
import htmlToImage from "html-to-image";
import download from "downloadjs";
export default {
  props: ["name", "file", "phone"],
  data() {
    return {
      imageData: ""
    };
  },
  mounted() {
    this.renderImage();
  },
  methods: {
    selectImage() {
      this.$refs.uploader.click();
    },
    renderImage() {
      const reader = new FileReader();
      reader.onload = e => {
        this.imageData = e.target.result;
      };
      reader.readAsDataURL(this.file);
    },
    async downloadCard(e) {
      e.preventDefault();
      const node = this.$refs.card;
      const dataURL = await htmlToImage.toPng(node);
      download(dataURL, "tarjeta.png");
    }
  }
};
</script>

<style scoped>
#container {
  display: grid;
  grid-template-rows: 1fr;
  grid-template-columns: 1fr;
  justify-items: center;
  align-items: center;
  font-family: "Avenir" sans-serif;
  color: #030200;
}

#background {
  grid-row: 1 / 2;
  grid-column: 1 / 2;
  width: 800px;
  height: 800px;
  background: url("../assets/img1.jpeg");
}

#uploader {
  display: none;
}

#picture {
  position: relative;
  width: 195px;
  height: 195px;
  border-radius: 500px;
  background-size: contain;
  left: 30px;
  top: 64px;
}

#name {
  position: relative;
  top: -55px;
  left: 325px;
  font-weight: bold;
  font-size: 40px;
  font-family: 'Avenir' sans-serif;
}

#phone {
  position: relative;
  font-weight: bold;
  font-size: 50px;
  top: 70px;
  left: 325px;
  font-family: 'Avenir' sans-serif;
}

#download-button {
  cursor: pointer;
  background: #4287f5;
  padding: 20px;
  width: 200px;
  display: flex;
  justify-content: center;
  box-shadow: grey;
  color: white;
}
</style>