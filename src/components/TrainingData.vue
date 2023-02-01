<template>
    <meta charset="utf-8">
    <link rel="stylesheet" href="styles.css">
    <h1>Standorte</h1>
    <h2>Wählen Sie einen Ort aus</h2>
  
  <div  v-if="mainToggle" class="allPictures">
    <figure>
      <img @click="fussballplatz" src="Fußballplatz.jpg" > 
      <figcaption>Fußballplatz</figcaption>
    </figure>

    <figure>
      <img @click="halle" src="Halle.jfif" >
      <figcaption>Kunstrasenhalle</figcaption>
    </figure>

    <figure>
      <img @click="joggen" src="JoggingstreckeWald.jpg" >
      <figcaption>Wald</figcaption>
    </figure>

    <figure>
      <img @click="kunstrasen" src="Kunstrasen.jpg" >
      <figcaption>Kunstrasen</figcaption>
    </figure>

    <figure>
      <img @click="regeneration" src="Regeneration.jpg" >
      <figcaption>Erholung / Sauna</figcaption>
    </figure>
  </div>

      <div  v-if="fussballToggle" class="card"> 
        <img src="Fußballplatz.jpg" alt=""> 
        <label for="1"> Intensität: </label>
        <input v-model="fussballplatzIntense" type="range" min="1" max="5" step="0.5" id="1" >
        <label for="2">Zeit in Stunden: </label>
        <input v-model="fussballplatzZeit" type="text" id="2">
        <button @click="mainSite">Zurück</button>
        <button @click="saveData">Bestätigen</button>
      </div>

      <div v-if="halleToggle" class="card"> 
        <img src="Halle.jfif"> 
        <label for="1"> Intensität: </label>
        <input v-model="HalleIntense" type="range" min="1" max="5" step="0.5" id="1">
        <label for="2">Zeit in Stunden: </label>
        <input v-model="HalleZeit" type="text" id="2">
        <button @click="mainSite">Zurück</button>
        <button @click="saveData">Bestätigen</button>
      </div>

      <div v-if="joggingToggle" class="card"> 
        <img src="JoggingstreckeWald.jpg"> 
        <label for="1"> Intensität: </label>
        <input v-model="WaldIntense" type="range" min="1" max="5" step="0.5" id="1">
        <label for="2">Zeit in Stunden: </label>
        <input v-model="WaldZeit" type="text" id="2">
        <button @click="mainSite">Zurück</button>
        <button @click="saveData">Bestätigen</button>
      </div>

      <div v-if="kunstToggle" class="card"> 
        <img src="Kunstrasen.jpg"> 
        <label for="1"> Intensität: </label>
        <input v-model="KunstrasenIntense" type="range" min="1" max="5" step="0.5" id="1">
        <label for="2">Zeit in Stunden: </label>
        <input v-model="KunstrasenZeit" type="text" id="2">
        <button @click="mainSite">Zurück</button>
        <button @click="saveData">Bestätigen</button>
      </div>

      <div v-if="regenerationToggle" class="card"> 
        <img src="Regeneration.jpg"> 
        <label for="1"> Intensität: </label>
        <input v-model="RegerenationIntense" type="range" min="1" max="5" step="0.5" id="1">
        <label for="2">Zeit in Stunden: </label>
        <input v-model="RegenerationZeit" type="text" id="2">
        <button @click="mainSite">Zurück</button>
        <button @click="saveData">Bestätigen</button>
      </div>




</template>

<script>

export default {
  data() {
    return {
      mainToggle: true,
      fussballToggle: false,
      halleToggle: false,
      joggingToggle: false,
      kunstToggle: false,
      regenerationToggle: false,
      fussballplatzIntense: 1,
      fussballplatzZeit: "",
      HalleIntense: 1,
      HalleZeit: "",
      WaldIntense: 1,
      WaldZeit: "",
      KunstrasenIntense: 1,
      KunstrasenZeit: "",
      RegenerationIntense: 1,
      RegenerationZeit: "",
      DataSave: {
        intensity: 0, 
        Zeit: "",
      }
    }
  },
  methods: {
    fussballplatz() {
      this.mainToggle = false
      this.fussballToggle = true
    },
    halle() {
      this.mainToggle = false
      this.halleToggle = true
    },
    joggen() {
      this.mainToggle = false
      this.joggingToggle = true
    },
    kunstrasen() {
      this.mainToggle = false
      this.kunstToggle = true
    },
    regeneration() {
      this.mainToggle = false
      this.regenerationToggle = true
    },
    mainSite() {
      this.mainToggle = true
      this.fussballToggle = false
      this.halleToggle = false
      this.joggingToggle = false
      this.kunstToggle = false
      this.regenerationToggle = false
    },
    saveData() {
      this.DataSave.push( {
        intensity: this.fussballplatzIntense, 
        Zeit: this.fussballplatzZeit
      } ) 
      console.log(this.DataSave);

    }
  }
}

//hat nicht alles so funktioniert wie ich wollte, habe Stunden mit dem Firebase verbrachgt aber es trotzdem nicht herausgefunden uns geschafft, vielleichgt wird es im
// laufe des Tages noch etwas und ich schaffe es funktionsfähig zu präsentieren
</script>
