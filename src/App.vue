<template>
  <div id="app">
    <div class="vuepdf">
      <h1 id="content">Content</h1>
      <div id="pdf">
        <button v-on:click="pdfgen">Generate PDF</button>
      </div>
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import pdfMake from "pdfmake";
import pdfFonts from "pdfmake/build/vfs_fonts.js";
export default {
  name: "App",
  props: {
    msg: String
  },
  components: {
    HelloWorld
  },
  methods: {
    pdfgen: function() {
      // var pdfMake = require('pdfmake/build/pdfmake.js')
      if (pdfMake.vfs === undefined) {
        // var pdfFonts = require('pdfmake/build/vfs_fonts.js')
        pdfMake.vfs = pdfFonts.pdfMake.vfs;
      }
      var docDefinition = "james";
      pdfMake.createPdf(docDefinition).download("optionalName.pdf");
    }
  }
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
