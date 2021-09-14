<template>
  <div id="app">
    <img src="./assets/ligneh.svg" width="10%"><br><br>
    <h1>Traducteur des codes missions de la ligne H</h1>
    <label>Code mission: <input maxlength="4" v-model="codeMission" type="text"></label>
    <p style="font-size: 2em;">{{ explainCode }}</p>
  </div>
</template>

<script>
export default {
  name: "codeExplainer",
  computed: {
    explainCode: function () {
      if(this.codeMission.length === 4) {
        let terminus;
        switch (this.codeMission[0]) {
          case "A":
            terminus="Paris";
            break

          case "B":
            terminus="Beauchamps";
            break

          case "O":
            terminus="Pontoise";
            break

          case "D":
            terminus="Saint-Denis";
            break

          case "L":
            terminus="Luzarches";
            break

          case "F":
            terminus="Saint-Leu-la-Forêt"
            break

          case "V":
            terminus="Valmondois";
            break

          case "P":
            terminus="Persan Beaumont"
            break

          case "M":
            terminus="Montsoult"
            break
        }
        let origine = "";
        switch (this.codeMission[3]) {
          case "A":
            origine="Paris";
            break

          case "O":
            origine="Pontoise";
            break

          case "B":
            origine="Beauchamps";
            break

          case "D":
            origine="Saint-Denis";
            break

          case "L":
            origine="Luzarches";
            break

          case "F":
            origine="Saint-Leu-la-Forêt"
            break

          case "V":
            origine="Valmondois";
            break

          case "P":
            origine="Persan Beaumont"
            break

          case "M":
            origine="Montsoult"
            break
        }
        let template = `Le train ${this.codeMission} part de ${origine} en direction ${terminus}.`

        let desserte = "";
        for (let i = 1; i < 3; i++) {
          switch (this.codeMission[i]) {
            case "O":
              desserte=" Il sera omnibus.";
              break

            case "R":
              desserte=" Il sera semi-direct."
              break
          }
        }
        template=template+desserte


        return template;
      } else {
        return "";
      }
    }
  },
  data() {
    let codeMission = "";
    return {
      codeMission
    }
  },
  watch:{
    codeMission: function(){
      this.codeMission = this.codeMission.toUpperCase();
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
